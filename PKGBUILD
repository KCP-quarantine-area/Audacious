_commit=ddfd82a8867a039460f923cd225b982935335ceb
pkgname=audacious
pkgver=3.10
pkgrel=1
pkgdesc="Lightweight, advanced audio player with qt5 interface"
arch=('x86_64')
url="https://audacious-media-player.org/"
license=('BSD')
depends=('qt5-base' 'libguess' 'libsm' 'unzip' 'hicolor-icon-theme' 'desktop-file-utils')
optdepends=('audacious-plugins')
makedepends=('python2')
source=(https://github.com/audacious-media-player/audacious/archive/${_commit}.zip)
md5sums=('479ef2a13e722abbd06d94c3a42b3c0a')

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
