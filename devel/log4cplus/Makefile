COMMENT=		logging API for C++

# XXX tried updating to 2.0.4 but net/kea doesn't exit properly
DISTNAME =		log4cplus-1.2.2
EXTRACT_SUFX=		.tar.bz2

SHARED_LIBS +=  log4cplus             3.0 # 0.0

CATEGORIES=		devel
HOMEPAGE=		http://log4cplus.sourceforge.net/

# Apache License 2.0 + BSD style
PERMIT_PACKAGE=	Yes

WANTLIB += c m pthread ${COMPILER_LIBCXX}

COMPILER =		base-clang ports-gcc base-gcc

SITES=			${SITE_SOURCEFORGE:=log4cplus/}

MODULES=		devel/cmake
#CXXFLAGS+=		-fPIC

.include <bsd.port.mk>
