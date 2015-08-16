# Maintainer: fordprefect <fordprefect@dukun.de>
pkgname=mediathekview
pkgver=9
pkgrel=1
pkgdesc="java-based downloader for several german broadcasting media centers (mediatheken), including ARD, ZDF, Arte, 3Sat, SWR, BR, MDR, NDR, WDR, HR, RBB, ORF, SF"
url="http://zdfmediathk.sourceforge.net/"
arch=('any')
license=('GPL3')
depends=('java-runtime' 'flvstreamer' )
optdepends=('ffmpeg' 'vlc')
source=("MediathekView_9.zip::http://sourceforge.net/projects/zdfmediathk/files/Mediathek/Mediathek%209/MediathekView_9.zip/download"
        "mediathekview.desktop"
        "mediathekview.png")
md5sums=('bc0db2078982b04a9686ad19f0bc9dab'
        '1dcb8f85104d2a91d85237146060b876'
        '560ce116608125b93e108ee20cd9ed96')

package() {
    # prepare environment
    mkdir -p "$pkgdir/opt/mediathekview" "$pkgdir/usr/bin"
    cd "$srcdir"
 
    # copy files and folders
    cp -r lib Icons "$pkgdir/opt/mediathekview/"
    install -m644 MediathekView.jar "$pkgdir/opt/mediathekview/"
    install -m644 MediathekView.ico "$pkgdir/opt/mediathekview/"

    # possibly unnecessary
    cp -r Anleitung "$pkgdir/opt/mediathekview/"
 
    # install .desktop and icon
    install -Dm644 mediathekview.desktop ${pkgdir}/usr/share/applications/mediathekview.desktop
    install -Dm644 mediathekview.png ${pkgdir}/usr/share/pixmaps/mediathekview.png

    # enable running start script from /usr/bin
    sed -i "s#./MediathekView.jar#/opt/mediathekview/MediathekView.jar#" MediathekView__Linux.sh
    install -m755 MediathekView__Linux.sh "$pkgdir/usr/bin/mediathekview"
}
