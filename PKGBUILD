pkgname=wps-office
pkgver=10.1.0.6757
pkgrel=1
pkgdesc="Kingsoft Office (WPS Office) is an office productivity suite"
arch=('x86_64')
license=("custom")
url="http://wps-community.org/"

depends=('fontconfig' 'xorg-mkfontdir' 'libxrender' 'desktop-file-utils' 'shared-mime-info' 'xdg-utils' 'glu' 'openssl' 'sdl2' 'pulseaudio' 'hicolor-icon-theme')

options=('!emptydirs')


source=("http://kdl.cc.ksosoft.com/wps-community/download/6757/wps-office_${pkgver}_x86_64.tar.xz"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_de_de.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_en_gb.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_es_es.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_es_mx.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_fr_ca.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_fr_fr.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_ja_jp.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_pl_pl.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_pt_br.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_pt_pt.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_ru_ru.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_zh_hk.7z"
        "http://kdl.cc.ksosoft.com/wps-community/download/mui/${pkgver}/mui_zh_tw.7z"
        )

sha1sums=('03a781599dfcf001fc3bcf1d49699bd1a44aaceb'
          '1aacee814a7bfb2619eac51ee612cb496eeb15da'
          '6933b8adf0f221fb4cff8eeefcb22294bb599a88'
          '64473529fd5e0a618c34da185e5d64d901c6fafa'
          '65effff3a9c2988ecb14342dcf1ae0246acd671f'
          '1aa9f37ff7fafd7f04ef59c4f291895d7da86030'
          'e42f8158a7c19eaa135e828177e542a6c54704eb'
          '54de758b1f30c355bfeccc29ee39c619c5eb8eca'
          'd6d88ea61eebd8ab4183cdb31aedd1e324e143e0'
          'c383790a33e5e3c25f18db574eabeaa9a267df40'
          'dcf53c88c6030317b1b62c262b089dfee30548b0'
          '72b21fcb3f9429c3989f869dbf773cf046a32b21'
          '246f7b826f68c1e63bfa43bdbfeb7aebd5b587ab'
          'a49555c732e987c24ff5ea055b8184bb06d10ee4')



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
    
    cp -r ${srcdir}/office6/mui/* "${pkgdir}/usr/lib/office6/mui"
}
