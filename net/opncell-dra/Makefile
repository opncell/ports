PORTNAME=       opncell-dra
DISTVERSION=    0.1.0
CATEGORIES=     net

MAINTAINER=     support@opncell.com
COMMENT=        OPNcell Diameter Routing Agent
WWW=            https://github.com/opncell/opncell

LICENSE=        BSD2CLAUSE

USES=           meson pkgconfig
USE_RC_SUBR=    opncell_dra
USE_GITHUB=     yes
GH_ACCOUNT=     opncell
GH_PROJECT=     opncell
GH_TAGNAME=     5116d8e

WRKSRC_SUBDIR=  dra

PLIST_FILES=    sbin/opncell-drad \
                "@sample ${ETCDIR}/dra.yaml.sample"
post-install:
	${MKDIR} ${STAGEDIR}${ETCDIR}
	${INSTALL_DATA} ${WRKSRC}/config/dra.yaml \
		${STAGEDIR}${ETCDIR}/dra.yaml.sample

.include <bsd.port.mk>
