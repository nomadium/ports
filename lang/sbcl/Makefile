# codegen for mips, mips64, riscv64, and sparc64 is present,
# but it needs some portage for OpenBSD.
ONLY_FOR_ARCHS +=	aarch64 amd64 arm i386 powerpc powerpc64

COMMENT =	high performance Common Lisp compiler

V =		2.3.9
DISTNAME =	sbcl-${V}-source
PKGNAME =	sbcl-${V}
REVISION =	0

CATEGORIES =	lang

HOMEPAGE =	https://www.sbcl.org/

MAINTAINER =	Sebastien Marie <semarie@kapouay.eu.org>

# Public domain and BSD
PERMIT_PACKAGE =	Yes

WANTLIB +=		c m util zstd

USE_WXNEEDED =		Yes
USE_NOEXECONLY =	Yes
USE_NOBTCFI =		Yes

SITES =			${SITE_SOURCEFORGE:=sbcl/}
EXTRACT_SUFX =		.tar.bz2
WRKDIST =		${WRKDIR}/sbcl-${V}

PSEUDO_FLAVORS =	native_bootstrap
FLAVOR ?=

# Supported bootstrap methods:
# - "ecl"   : default (for portability)
# - "clisp" : build might be faster than with ecl
# - "sbcl"  : for native bootstrap
#
# For testing, it could be manually overrided by passing
# BOOTSTRAP_METHOD=xxx on make command-line.

BOOTSTRAP_METHOD-amd64	=	clisp
BOOTSTRAP_METHOD-powerpc =	clisp
BOOTSTRAP_METHOD-${MACHINE_ARCH} ?=	ecl

BOOTSTRAP_METHOD ?=	${BOOTSTRAP_METHOD-${MACHINE_ARCH}}

.if ${FLAVOR:Mnative_bootstrap}
BOOTSTRAP_METHOD =	sbcl
.endif

.if ${BOOTSTRAP_METHOD:Msbcl}
BUILD_DEPENDS +=	lang/sbcl
XCHOST_CMD =		${LOCALBASE}/bin/sbcl \
				--disable-debugger --no-sysinit --no-userinit

.elif ${BOOTSTRAP_METHOD:Mclisp}
BUILD_DEPENDS +=	lang/clisp
XCHOST_CMD =		${LOCALBASE}/bin/clisp -q -norc

.elif ${BOOTSTRAP_METHOD:Mecl}
BUILD_DEPENDS +=	lang/ecl
XCHOST_CMD =		${LOCALBASE}/bin/ecl -q --norc

.else
ERRORS +=	"Fatal: unknown BOOTSTRAP_METHOD"
.endif

# sb-thread is not available everywhere
SB_THREAD-${MACHINE_ARCH} ?=	Yes
SB_THREAD-arm =		No
SB_THREAD-i386 =	No

.if ${SB_THREAD-${MACHINE_ARCH}:MYes}
EXTRA_PARAMS +=		--with-sb-thread
WANTLIB +=		pthread
.else
EXTRA_PARAMS +=		--without-sb-thread
.endif

BUILD_DEPENDS +=	print/texinfo
LIB_DEPENDS +=		archivers/zstd
TEST_DEPENDS +=		devel/capstone/main \
			devel/gmp

MAKE_ENV +=		CFLAGS="${CFLAGS} -I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib" \
			LINKFLAGS="-L${LOCALBASE}/lib" \
			MAKEINFO=${PREFIX}/bin/gmakeinfo \
			MAN_DIR="${PREFIX}/man/" \
			INFO_DIR="${PREFIX}/info/"

USE_GMAKE =		Yes

DEBUG_PACKAGES =	${BUILD_PACKAGES}

do-configure:
	printf '"%s.%s.%s"\n' "${V}" "openbsd" "${FULLPKGNAME}" \
		>${WRKSRC}/version.lisp-expr

do-build:
	umask 022 && cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} \
		/bin/sh ./make.sh \
			--prefix="${PREFIX}" \
			--xc-host="${XCHOST_CMD}" \
			--with-sb-core-compression \
			--with-sb-xref-for-internals \
			${EXTRA_PARAMS}
	umask 022 && cd ${WRKSRC}/doc/manual/ && ${SETENV} ${MAKE_ENV} \
		${GMAKE} info

do-install:
	cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} \
		/bin/sh ./install.sh \
			--prefix="${PREFIX}"

post-install:
	rmdir ${PREFIX}/share/doc/sbcl/html/

do-test:
	cd ${WRKSRC}/tests/ && ${SETENV} ${MAKE_ENV} /bin/sh ./run-tests.sh

.include <bsd.port.mk>
