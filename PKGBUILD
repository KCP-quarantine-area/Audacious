_commit=6c9caba7bbaf9076eb0cf38ae14730b5c2d1f7fc
pkgname=audacious
pkgver=3.8.1
pkgrel=1
pkgdesc="Lightweight, advanced audio player with qt5 interface"
arch=('x86_64')
url="http://audacious-media-player.org/"
license=('BSD')
depends=('qt5-base' 'libguess' 'libsm' 'unzip'
         'hicolor-icon-theme' 'desktop-file-utils')
makedepends=('python2') # for gdbus-codegen
optdepends=('audacious-plugins: many helpful plugins')
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
