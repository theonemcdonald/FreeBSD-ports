# Created by: Alexander Nusov <alexander.nusov@nfvexpress.com>

PORTNAME=	python-openstackclient
PORTVERSION=	5.2.1
CATEGORIES=	net python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	OpenStack Command-line Client

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}pbr>=2.0.0:devel/py-pbr@${PY_FLAVOR}
RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}Babel>=2.3.4:devel/py-babel@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}cliff>=2.8.0:devel/py-cliff@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}openstacksdk>=0.36.0:devel/py-openstacksdk@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}osc-lib>=2.0.0:devel/py-osc-lib@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}oslo.i18n>=3.15.3:devel/py-oslo.i18n@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}oslo.utils>=3.33.0:devel/py-oslo.utils@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}pbr>=2.0.0:devel/py-pbr@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}python-cinderclient>=3.3.0:net/py-python-cinderclient@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}python-keystoneclient>=3.22.0:net/py-python-keystoneclient@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}python-novaclient>=15.1.0:net/py-python-novaclient@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}six>=1.10.0:devel/py-six@${PY_FLAVOR}

USES=		python:3.6+ shebangfix
USE_PYTHON=	autoplist concurrent distutils

NO_ARCH=	yes

SHEBANG_GLOB=	*.sh

.include <bsd.port.mk>
