COMMENT=		simple paint program

DISTNAME=		xpaint-2.7.8.1
REVISION=		5
CATEGORIES=		graphics x11

HOMEPAGE=		http://sf-xpaint.sourceforge.net/

SITES=			${SITE_SOURCEFORGE:=sf-xpaint/}
EXTRACT_SUFX=		.tar.bz2

# MIT
PERMIT_PACKAGE=	Yes

WANTLIB=		ICE SM X11 Xau Xdmcp Xaw Xext Xmu Xpm Xt c m \
			z jpeg>=62 tiff>=36 png>=4

LIB_DEPENDS=		graphics/jpeg \
			graphics/tiff \
			graphics/png

CONFIGURE_STYLE= 	imake
ALL_TARGET=		xaw
NO_TEST=		Yes

.include <bsd.port.mk>
