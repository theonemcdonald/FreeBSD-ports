# Created by: DarwinSurvivor <darwinsurvivor@gmail.com>

PORTNAME=	notmuch
PORTVERSION=	0.32
PORTREVISION?=	0
CATEGORIES?=	mail
MASTER_SITES=	https://notmuchmail.org/releases/

MAINTAINER=	dbaio@FreeBSD.org
COMMENT?=	Thread-based email index, search and tagging application

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/${WRKSRC_SUBDIR:C/[^\/]+/../g}/COPYING-GPL-3

.ifndef MASTERDIR
LIB_DEPENDS=	libgmime-3.0.so:mail/gmime30 \
		libxapian.so:databases/xapian-core \
		libtalloc.so:devel/talloc
TEST_DEPENDS=	bash:shells/bash \
		emacs:editors/emacs@nox \
		dtach:misc/dtach \
		gdate:sysutils/coreutils \
		gbase64:sysutils/coreutils \
		gsed:textproc/gsed \
		gsha256sum:sysutils/coreutils \
		gpg:security/gnupg \
		gwc:sysutils/coreutils \
		${LOCALBASE}/bin/gdb:devel/gdb

USES=		compiler:c++11-lang gmake gnome pkgconfig python:3.5+,build,test
USE_GNOME=	glib20
USE_LDCONFIG=	yes
.endif

USES+=		tar:xz

.ifndef MASTERDIR
HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	--infodir=${PREFIX}/${INFO_PATH} \
		--mandir=${MANPREFIX}/man \
		--prefix=${PREFIX} \
		--with-bash-completion \
		--with-retry-lock \
		--with-zsh-completion \
		--without-emacs
CONFIGURE_ENV+=	PYTHON=${PYTHON_CMD}
TEST_ENV+=	NOTMUCH_SKIP_TESTS="basic.12 count.14 insert.2[89] insert.3[0-9] message-property.6 regexp-query.21" \
		TEST_CFLAGS="-g -O0 -I${LOCALBASE}/include -L${LOCALBASE}/lib" \
		TEST_GDB=${LOCALBASE}/bin/gdb \
		V=1
TEST_TARGET=	test
.endif

PATCH_WRKSRC=	${WRKSRC}/${WRKSRC_SUBDIR:C/[^\/]+/../g}
PKGDIR=		${.CURDIR}

.ifndef MASTERDIR
OPTIONS_DEFINE=	DOXYGEN MANPAGES
OPTIONS_DEFAULT=	MANPAGES
OPTIONS_SUB=	yes

DOXYGEN_BUILD_DEPENDS=	doxygen:devel/doxygen
DOXYGEN_CONFIGURE_WITH=	api-docs
MANPAGES_BUILD_DEPENDS=	sphinx-build:textproc/py-sphinx
MANPAGES_CONFIGURE_WITH=	docs

PORTSCOUT=	limit:^[0-9\.]*$$

# Avoid conflict with C++20 <version> by ignoring <...> under WRKSRC
post-patch:
	@${REINPLACE_CMD} -i .c++20 's/-I$$(srcdir)/-iquote$$(srcdir)/' \
		${WRKSRC}/*/Makefile.local

# Install bash completions without incurring a dependency on
# shells/bash-completion.
post-configure:
	${REINPLACE_CMD} \
		-e '/^BASH_ABSOLUTE[[:blank:]]*=/s|=.*|=${LOCALBASE}/bin/bash|' \
		-e '/^HAVE_BASH[[:blank:]]*=/s/=.*/=1/' \
		-e '/^WITH_BASH[[:blank:]]*=/s/=.*/=1/' \
		${WRKSRC}/Makefile.config

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/notmuch
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/libnotmuch.so.?*.?*.?*

# Keep poudriere-testport(8) happy.
post-install-MANPAGES-on:
	@${RM} ${STAGEDIR}${MANPREFIX}/man/man1/notmuch-emacs-mua.1.gz
.endif

.include <bsd.port.mk>
