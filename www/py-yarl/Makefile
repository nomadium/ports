COMMENT =		yet another URL library

MODPY_EGG_VERSION =	1.4.2
DISTNAME =		yarl-${MODPY_EGG_VERSION}
PKGNAME =		py-${DISTNAME}
REVISION =		6

CATEGORIES =		www devel

HOMEPAGE =		https://yarl.readthedocs.org

MAINTAINER =		Joerg Jung <jung@openbsd.org>

# Apache License 2.0
PERMIT_PACKAGE =	Yes

WANTLIB += pthread ${MODPY_WANTLIB}

MODULES =		lang/python
FLAVORS =		python3
FLAVOR =		python3

MODPY_PI =		Yes
MODPY_PYBUILD =		setuptools

RUN_DEPENDS =		net/py-idna${MODPY_FLAVOR}>=2.0 \
			www/py-multidict${MODPY_FLAVOR}>=4.0
TEST_DEPENDS =		devel/py-test-runner${MODPY_FLAVOR}

.include <bsd.port.mk>
