PORTNAME=       os-cellular
PORTVERSION=    26.7.0
CATEGORIES=     net-mgmt

MAINTAINER=     support@ds.co.ug
COMMENT=        OPNcell Open5GS management plugin for OPNsense
WWW=            https://github.com/opncell/opncell

LICENSE=        BSD2CLAUSE
USES=           python:run shebangfix
SHEBANG_FILES=  src/opnsense/scripts/opncore/*.py \
                src/opnsense/scripts/opncore/*.sh

USE_GITHUB=     yes
GH_ACCOUNT=     opncell
GH_PROJECT=     opncell
GH_TAGNAME=     v26.7

RUN_DEPENDS=	bash:shells/bash \
                open5gs>=2.8.0:net/opncell-open5gs \
                mongodb80>=8.0.29:databases/mongodb80
NO_BUILD=       yes
NO_ARCH=        yes

WRKSRC_SUBDIR=  opncell

.include <bsd.port.mk>
