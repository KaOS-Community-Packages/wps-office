pkgname=wps-office
pkgver=10.1.0.6634
pkgrel=1
pkgdesc="Kingsoft Office (WPS Office) is an office productivity suite"
arch=('x86_64')
license=("custom")
url="http://wps-community.org/"
depends=('fontconfig' 'libxrender' 'desktop-file-utils' 'shared-mime-info' 'xdg-utils' 'glu' 'openssl' 'sdl2' 'pulseaudio' 'hicolor-icon-theme' 'cups' 'pango' 'curl' 'libjpeg-turbo')
options=('!emptydirs')
install=${pkgname}.install
source=("http://kdl.cc.ksosoft.com/wps-community/download/6634/wps-office_${pkgver}_x86_64.tar.xz")
sha1sums=('afdbf0b8667777f2266ba9231414dcf35e3d1cc1')
PKGEXT=".pkg.tar"

prepare() {
    cd wps-office_${pkgver}_x86_64
    sed -i 's|/opt/kingsoft/wps-office|/usr/lib|' wps wpp et
    sed -i 's|/office6/${gApp}  ${gOptExt}|/office6/${gApp} -style gtk+ ${gOptExt}|' wps
    sed -i 's|/office6/${gApp} ${gOptExt}|/office6/${gApp} -style gtk+ ${gOptExt}|' wpp et
}

package() {
    cd wps-office_${pkgver}_x86_64

    install -d "${pkgdir}/usr/lib"
    cp -r office6 "${pkgdir}/usr/lib"

    install -d "${pkgdir}/usr/bin"
    install -m755 wps wpp et "${pkgdir}/usr/bin"

    install -d "${pkgdir}/usr/share/applications"
    cp -r resource/applications/* "${pkgdir}/usr/share/applications"

    install -d "${pkgdir}/usr/share/icons"
    cp -r resource/icons/* "${pkgdir}/usr/share/icons"

    install -d "${pkgdir}/usr/share/mime"
    cp -r resource/mime/* "${pkgdir}/usr/share/mime"

    install -d "${pkgdir}/usr/share/fonts/wps-office"
    cp -r fonts/* "${pkgdir}/usr/share/fonts/wps-office"

    install -Dm644 office6/mui/default/EULA.txt "${pkgdir}/usr/share/licenses/$pkgname/EULA.txt"
}
