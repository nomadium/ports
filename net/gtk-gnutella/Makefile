COMMENT=		Gtk-based GUI client for the Gnutella Network

DISTNAME=		gtk-gnutella-0.97.1
EPOCH=			0
CATEGORIES=		net
REVISION=		7
FIX_EXTRACT_PERMISSIONS=Yes

# this litle shit has its own mkdep that stashes /usr/local dependencies
# in makefiles
DPB_PROPERTIES =	nojunk

HOMEPAGE=		http://gtk-gnutella.sourceforge.net/

# GPLv2+
PERMIT_PACKAGE=	Yes

WANTLIB =  X11 Xcomposite Xcursor Xdamage Xext Xfixes Xi Xinerama Xrandr
WANTLIB += Xrender atk-1.0 c cairo fontconfig freetype gdk-x11-2.0
WANTLIB += gdk_pixbuf-2.0 gio-2.0 glib-2.0 gobject-2.0 gtk-x11-2.0
WANTLIB += harfbuzz iconv intl m pango-1.0 pangocairo-1.0 pangoft2-1.0
WANTLIB += pthread z

SITES=		${SITE_SOURCEFORGE:=gtk-gnutella/}
EXTRACT_SUFX=	.tar.bz2

BUILD_DEPENDS=	devel/gettext,-tools
LIB_DEPENDS=	x11/gtk+2
RUN_DEPENDS=	devel/desktop-file-utils

CONFIGURE_STYLE= simple
CONFIGURE_SCRIPT=Configure
# -d don't run interactively
# -e fixes bulk package build
CONFIGURE_ARGS=	-d  -e \
		-D mansrc="${PREFIX}/man/man1" \
		-D prefix="${PREFIX}" \
		-D privlib="${PREFIX}/share/gtk-gnutella" \
		-D cc="${CC}" \
		-D ccflags="${CFLAGS} -I${LOCALBASE}/include" \
		-D gtkversion="2" \
		-D ldflags="-L${LOCALBASE}/lib -liconv" \
		-D official="true" \
		-D yacc="yacc" \
		-U d_dbus \
		-U d_gnutls \
		-U d_remotectrl \
		-U d_sqlite \
		-U optimize

MAKE_FLAGS=	GNUTLS_LDFLAGS= GNUTLS_CFLAGS=
DESTDIRNAME=	INSTALL_PREFIX
INSTALL_TARGET=	install install.man

NO_TEST=	Yes

.include <bsd.port.mk>
