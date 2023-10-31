COMMENT=		debugging tool for Python

MODPY_EGG_VERSION=	2.1.3
DISTNAME=		icecream-${MODPY_EGG_VERSION}
PKGNAME=		py-${DISTNAME}
CATEGORIES=		devel

HOMEPAGE=		https://github.com/gruns/icecream

MAINTAINER=		Miguel Landaeta <miguel@miguel.cc>

# MIT
PERMIT_PACKAGE=		Yes

MODULES=		lang/python

MODPY_PI=		Yes
MODPY_PYBUILD=		setuptools
MODPY_PYTEST=		No
MODPY_SETUPUTILS=	Yes
MODPY_SETUP_ARGS=	test
SEPARATE_BUILD=		Yes

RUN_DEPENDS=		devel/py-asttokens${MODPY_FLAVOR} \
			devel/py-colorama${MODPY_FLAVOR} \
			devel/py-executing${MODPY_FLAVOR} \
			textproc/py-pygments${MODPY_FLAVOR}

FLAVORS=		python3
FLAVOR=			python3

.include <bsd.port.mk>
