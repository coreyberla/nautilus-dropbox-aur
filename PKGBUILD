# Maintainer:   Corey Berla <corey@berla.me>
# Contributor:  M.Reynolds <blackboxnetworkproject@gmail.com>
# Contributor:  Vlad M. <vlad@archlinux.net>
# Contributor:  Christophe Gueret <christophe.gueret@gmail.com>
# Contributor:  josephgbr <rafael.f.f1@gmail.com>
# Contributor:  cmorlok <christianmorlok@web.de>
# Contributor:  fazibear <fazibear@gmail.com>
# Contributor:  neuromante <lorenzo.nizzi.grifi@gmail.com>
# Contributor:  Gordin <9ordin @t gmail.com>

pkgname=nautilus-dropbox
pkgdesc="Dropbox Nautilus Extension"
pkgver=2020.03.04.daf0de29
pkgrel=1
arch=(x86_64)
url="https://www.dropbox.com/"
license=('custom:CC-BY-ND-3' 'GPL')
depends=(nautilus libnautilus-extension dropbox)
makedepends=(python python-docutils python-gobject gnome-common)
options=('!libtool' '!emptydirs')
_commit=e5dd94738b096c1d7c131365e99b19c9daf0de29
source=("git+https://github.com/dropbox/nautilus-dropbox.git#commit=$_commit"
	"nautilus43.patch")
sha256sums=('SKIP' 
	    '1c65352746b31ee09a5ecb00124df650ddbe82daea5bcef76e9c379762943faa')

build() {
    cd nautilus-dropbox
    git apply ../nautilus43.patch
    ./autogen.sh
    make
}

package() {
    cd nautilus-dropbox
    make DESTDIR="$pkgdir" install

    # install the common license
    install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"

    # remove executables and depend on 'dropbox' package
    rm "$pkgdir/usr/bin/dropbox"
    rm "$pkgdir/usr/share/applications/dropbox.desktop"
    rm "$pkgdir/usr/share/man/man1/dropbox.1"
}
