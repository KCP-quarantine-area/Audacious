_commit=7e86bd7d03300bfd5284b266cde4d4fa1d59a33d
pkgname=audacious
pkgver=3.9
pkgrel=1
pkgdesc="Lightweight, advanced audio player with qt5 interface"
arch=('x86_64')
url="http://audacious-media-player.org/"
license=('BSD')
depends=('qt5-base' 'libguess' 'libsm' 'unzip' 'hicolor-icon-theme' 'desktop-file-utils')
optdepends=('audacious-plugins')
makedepends=('python2')
source=(https://github.com/audacious-media-player/audacious/archive/${_commit}.zip)
md5sums=('dede04ec97f35d6f182d9d7c907dd118')

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
