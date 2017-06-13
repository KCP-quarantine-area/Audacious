_commit=7886b7be794e52bc2efe509f450c0881919946b2
pkgname=audacious
pkgver=3.8.2
pkgrel=1
pkgdesc="Lightweight, advanced audio player with qt5 interface"
arch=('x86_64')
url="http://audacious-media-player.org/"
license=('BSD')
depends=('qt5-base' 'libguess' 'libsm' 'unzip'
         'hicolor-icon-theme' 'desktop-file-utils')
makedepends=('python2') # for gdbus-codegen
optdepends=('audacious-plugins-jack: many helpful plugins including jack')
            #OR
            'audacious-plugins-jack2: many helpful plugins including jack')
source=(https://github.com/audacious-media-player/audacious/archive/${_commit}.zip)
md5sums=('2d959d99a971f793a1dbbc6176ec39ed')

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
