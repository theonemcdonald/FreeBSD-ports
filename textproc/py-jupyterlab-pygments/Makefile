# Created by: Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	jupyterlab-pygments
PORTVERSION=	0.1.2
CATEGORIES=	textproc python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	jupyterlab_pygments-${PORTVERSION}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Pygments theme using JupyterLab CSS variables

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}pygments>=2.4.1<3:textproc/py-pygments@${PY_FLAVOR}

USES=		python:3.6+
USE_PYTHON=	autoplist concurrent distutils

NO_ARCH=	yes

.include <bsd.port.mk>
