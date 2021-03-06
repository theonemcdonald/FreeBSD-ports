# Created by: Koop Mast <kwm@FreeBSD.org>

PORTNAME=	accountsservice
PORTVERSION=	0.6.42
CATEGORIES=	sysutils devel
MASTER_SITES=	http://www.freedesktop.org/software/${PORTNAME}/

MAINTAINER=	kwm@FreeBSD.org
COMMENT=	D-Bus interface for user account query and manipulation

LICENSE=	GPLv3+
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libdbus-glib-1.so:devel/dbus-glib \
		libpolkit-gobject-1.so:sysutils/polkit

USE_GNOME=	glib20 intlhack introspection:build libxslt
USES=		cpe gettext gmake gnome libtool localbase:ldflags pathfix \
		pkgconfig tar:xz
CPE_VENDOR=	ray_stode
GNU_CONFIGURE=	yes
USE_LDCONFIG=	yes
CONFIGURE_ARGS=	--disable-systemd --localstatedir=/var/
INSTALL_TARGET=	install-strip

# XXX HACK! this file isn't present on the pristine jails of the builders
# and configure breaks without it. Beter solutions welcome.
.if defined(PACKAGE_BUILDING)
CONFIGURE_ENV+=	ac_cv_file__var_log_utx_log=yes
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|/etc/gdm/custom.conf|${LOCALBASE}/etc/gdm/custom.conf|g' \
		${WRKSRC}/src/daemon.c
	@${REINPLACE_CMD} -e 's|/lib/AccountsService|/db/AccountsService|g' \
		${WRKSRC}/src/user.c ${WRKSRC}/src/Makefile.in

.include <bsd.port.mk>
