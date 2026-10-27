PORTNAME=       opncell-dra
DISTVERSION=    0.1.0
CATEGORIES=     net

MAINTAINER=     support@opncell.com
COMMENT=        OPNcell Diameter Routing Agent
WWW=            https://github.com/opncell/opncell

LICENSE=        BSD2CLAUSE

BUILD_DEPENDS=  ${LOCALBASE}/lib/libgcrypt.so:security/libgcrypt

LIB_DEPENDS=    libgnutls.so:security/gnutls \
                libidn.so:dns/libidn \
                libyaml.so:textproc/libyaml

USES=           bison localbase:ldflags meson pkgconfig
USE_RC_SUBR=    opncell_dra
USE_GITHUB=     yes
GH_ACCOUNT=     opncell
GH_PROJECT=     opncell
GH_TAGNAME=     44ec93b
GH_TUPLE=       open5gs:freeDiameter:r1.5.0:freediameter

WRKSRC_SUBDIR=  dra

PLIST_FILES=    sbin/opncell-drad \
                "@sample ${ETCDIR}/dra.yaml.sample"
post-extract:
	${RMDIR} ${WRKSRC}/subprojects/freeDiameter 2>/dev/null || ${TRUE}
	${CP} -R ${WRKSRC_freediameter} ${WRKSRC}/subprojects/freeDiameter
	${PATCH} -d ${WRKSRC}/subprojects/freeDiameter -p1 < \
		${WRKSRC}/subprojects/packagefiles/freeDiameter-freebsd-basename.patch
	${PATCH} -d ${WRKSRC}/subprojects/freeDiameter -p1 < \
		${WRKSRC}/subprojects/packagefiles/freeDiameter-freebsd-sctp.patch
	${PATCH} -d ${WRKSRC}/subprojects/freeDiameter -p1 < \
		${WRKSRC}/subprojects/packagefiles/freeDiameter-dynamic-peer-remove.patch
do-install:
	${INSTALL_PROGRAM} ${BUILD_WRKSRC}/opncell-drad \
		${STAGEDIR}${PREFIX}/sbin/opncell-drad
	${MKDIR} ${STAGEDIR}${ETCDIR}
	${INSTALL_DATA} ${WRKSRC}/config/dra.yaml \
		${STAGEDIR}${ETCDIR}/dra.yaml.sample

.include <bsd.port.mk>
