pkgname=wps-office
pkgver=10.1.0.6757
pkgrel=1
pkgdesc="Kingsoft Office (WPS Office) is an office productivity suite"
arch=('x86_64')
license=("custom")
url="http://wps-community.org/"

depends=('fontconfig' 'xorg-mkfontdir' 'libxrender' 'desktop-file-utils' 'shared-mime-info' 'xdg-utils' 'glu' 'openssl' 'sdl2' 'pulseaudio' 'hicolor-icon-theme')

options=('!emptydirs')
install=${pkgname}.install

source=("http://kdl.cc.ksosoft.com/wps-community/download/6757/wps-office_${pkgver}_x86_64.tar.xz")
sha1sums=('03a781599dfcf001fc3bcf1d49699bd1a44aaceb')


prepare() {
    cd wps-office_${pkgver}_${arch}

    sed -i 's|/opt/kingsoft/wps-office|/usr/lib|' wps wpp et
}

package() {
    cd wps-office_${pkgver}_${arch}

    install -d "${pkgdir}/usr/lib"
    cp -r office6 "${pkgdir}/usr/lib"

    install -d "${pkgdir}/usr/bin"
    install -m755 wps wpp et "${pkgdir}/usr/bin"

    install -d "${pkgdir}/usr/share/applications"
    cp -r resource/applications/* "${pkgdir}/usr/share/applications"

    install -d "${pkgdir}/usr/share/icons"
    cp -r resource/icons/* "${pkgdir}/usr/share/icons"

    install -d "${pkgdir}/usr/share/fonts/wps-office"

    install -Dm644 office6/mui/default/EULA.txt "${pkgdir}/usr/share/licenses/$pkgname/EULA.txt"
}
