COMMENT =	Qt-based library for writing accessibility apps

DISTNAME =	libqaccessibilityclient-0.4.1
REVISION =	0

SHARED_LIBS +=	qaccessibilityclient-qt5  1.0 # 0.3

CATEGORIES =	x11 devel

MAINTAINER =	Rafael Sadowski <rsadowski@openbsd.org>

# LGPLv2.1+
PERMIT_PACKAGE =	Yes

WANTLIB += ${COMPILER_LIBCXX} Qt5Core Qt5DBus Qt5Gui Qt5Widgets
WANTLIB += c m

SITES =		${SITE_KDE:=stable/libqaccessibilityclient/}

EXTRACT_SUFX =	.tar.xz

MODULES =	devel/kf5

TEST_IS_INTERACTIVE =	X11

.include <bsd.port.mk>
