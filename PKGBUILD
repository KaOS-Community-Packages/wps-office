pkgname=wps-office
pkgver=10.1.0.5707_a21
_pkgver=10.1.0.5707~a21
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
source=("http://kdl.cc.ksosoft.com/wps-community/download/a21/wps-office_${_pkgver}_x86_64.tar.xz")
sha256sums=('aa875a06e7eef79a30d6e5a4bd03f08eeb1524013edd59122d95a20b1638d9c5')

PKGEXT=".pkg.tar"

prepare() {
  cd wps-office_${_pkgver}_${arch}

  sed -i 's|/opt/kingsoft/wps-office|/usr/lib|' wps wpp et
}

package() {
  cd wps-office_${_pkgver}_${arch}

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
