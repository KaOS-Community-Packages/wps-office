pkgname=wps-office
pkgver=10.1.0.5460_a20p1
_pkgver=10.1.0.5460~a20p1
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
source=("http://kdl.cc.ksosoft.com/wps-community/download/a20/wps-office_${_pkgver}_x86_64.tar.xz"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/10.1.0.5444/mui_es_es.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/10.1.0.5444/mui_es_mx.7z"
        "http://wps-community.org/download/dicts/es_ES.zip")
sha512sums=('769fd003522a8654731d86c24b35623a916327018c0ee788448635480beb4fe9c192605668e9d7fdbd4c04de5806fe95a9689cd6e1034d51942cd740fe1795e0'
            'c8d40cf2f44d8d7734a0206d72c8f82763048cb3c724ef7dd1a209ed1eb500d0bea686f7bdfac948c99a522d8138471fd7dde32625a83d43aecd7efd7b9ac0bd'
            '921769aa5a734423a1ab508ef8d914ca16b9ffddb94d51f9c43bb830d07bab1bfc373efaf017c0fc07fe5e1f24ed78584d7e28b0e5816073d932b8af4167fa3c'
            '0c9cae3f4bae8c61eb6c6c060f12271d20f383b453387c1e3c829bb79fd309b83ac3d655a10ad57f88d8637f18903361bdb4b04660a563ee84b56b6f4f1cef01')

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

# Add UI language and Spellcheck Spanish support
  cd $srcdir

  cp -r office6 "$pkgdir/usr/lib"
  cp -r es_ES "$pkgdir/usr/lib/office6/dicts"
}
