_commit=abcd04c88d6a4b899ee576b274e208736f61e116
pkgname=audacious
pkgver=3.7.2
pkgrel=1
pkgdesc="Lightweight, advanced audio player with qt5 interface"
arch=('x86_64')
url="http://audacious-media-player.org/"
license=('BSD')
depends=('qt5-base' 'libguess' 'libsm' 'unzip'
         'hicolor-icon-theme' 'desktop-file-utils')
makedepends=('python2') # for gdbus-codegen
optdepends=('audacious-plugins-qt5: many helpful plugins')
source=(https://github.com/audacious-media-player/audacious/archive/${_commit}.zip)
md5sums=('5eb1ce23a1ed4f36641c9ff764382f67')

build() {
  cd "$srcdir/$pkgname-$_commit"

./autogen.sh 
  ./configure \
    --prefix=/usr \
    --with-buildstamp='KaOS' \
    --enable-qt \
    --disable-gtk \
    --disable-modplug \
    --disable-gnomeshortcuts \
    --disable-adplug
  make
}

package() {
  cd "$srcdir/$pkgname-$_commit"
  make DESTDIR="$pkgdir" install
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/qt5/LICENSE"
}
