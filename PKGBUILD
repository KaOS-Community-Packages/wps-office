pkgname=wps-office
pkgver=10.1.0.5503_a20p2
_pkgver=10.1.0.5503
_pkgrel=~a20p2
pkgrel=1
pkgdesc="WPS Office is an office productivity suite"
arch=('x86_64')
license=("custom")
url="http://wps-community.org/"
depends=('fontconfig' 'libpng12' 'glib2' 'libsm' 'libxext' 'libxrender' 'libxml2' 'desktop-file-utils' 'shared-mime-info' 'xdg-utils' 'glu')
optdepends=('cups: for printing support'
            'pango: for complex (right-to-left) text support')
options=('!emptydirs')
install=${pkgname}.install
source=("http://kdl.cc.ksosoft.com/wps-community/download/a20/wps-office_${_pkgver}${_pkgrel}_x86_64.tar.xz")
sha512sums=('e6e8802bb95b578ca3f2f39876855a8c74177057fa515f54b72c7fc357aad31a50efe9ca6beae6d04a3bc3036e4184d045e0fa29bee6c586e5bc52675c9c3053')

PKGEXT=".pkg.tar"

prepare() {
  cd wps-office_${_pkgver}${_pkgrel}_${arch}

  sed -i 's|/opt/kingsoft/wps-office|/usr/lib|' wps wpp et
}

package() {
  cd wps-office_${_pkgver}${_pkgrel}_${arch}

  install -d "$pkgdir/usr/lib"
  cp -r office6 "$pkgdir/usr/lib"

  install -d "$pkgdir/usr/bin"
  install -m755 wps wpp et "$pkgdir/usr/bin"

  install -d "$pkgdir/usr/share/applications"
  cp -r resource/applications/* "$pkgdir/usr/share/applications"

  install -d "$pkgdir/usr/share/icons"
  cp -r resource/icons/* "$pkgdir/usr/share/icons"

  install -d "$pkgdir/usr/share/mime"
  cp -r resource/mime/* "$pkgdir/usr/share/mime"

  install -d "$pkgdir/usr/share/fonts/wps-office"
  cp -r fonts/* "$pkgdir/usr/share/fonts/wps-office"

  install -Dm644 office6/mui/default/EULA.txt "$pkgdir/usr/share/licenses/$pkgname/EULA.txt"
}
