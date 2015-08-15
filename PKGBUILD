# Maintainer : philefou <tuxication AT gmail DOT com>
# Contributor: lindquist <tomas@famolsen.dk>
# Contributor: Christoph Siegenthaler <csi@gmx.ch>
# Contributor: Mihai Militaru <mihai.militaru@ephemeros.org>
# Contributor: SpepS <dreamspepser at yahoo dot it>

pkgname=glfw
pkgver=2.7.2
pkgrel=2
pkgdesc="A free, open source, portable framework for OpenGL application development."
arch=('i686' 'x86_64')
url="http://www.glfw.org/"
license=('custom:ZLIB')
depends=('libgl' 'libxrandr')
source=("http://switch.dl.sourceforge.net/sourceforge/$pkgname/$pkgname-$pkgver.tar.bz2")
md5sums=('bb4f33b43e40f8cd3015a653dca02ed1')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  make x11
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make PREFIX="$pkgdir/usr" x11-dist-install

  # license
  install -Dm644 COPYING.txt \
    "$pkgdir/usr/share/licenses/$pkgname/COPYING"

  # docs
  install -d "$pkgdir/usr/share/doc/$pkgname"
  install -Dm644 docs/*.pdf "$pkgdir/usr/share/doc/$pkgname"

  # fix pc file prefix path
  sed -i "s|$pkgdir||g" "$pkgdir/usr/lib/pkgconfig/lib$pkgname.pc"
}
