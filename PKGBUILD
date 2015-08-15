# Maintainer: Tofe <chris.chapuis@gmail.com>
# Contributor: 4javier
# Contributor: snoopy33

pkgname=cairo-dock
pkgver=3.2.0
pkgrel=0
pkgdesc="A light eye-candy fully themable animated dock for any Linux desktop. It has a family-likeness with OSX dock, but with more options."
url="https://launchpad.net/cairo-dock-core"
license="GPL"
arch=('i686' 'x86_64')
depends=('cairo' 'librsvg' 'dbus-glib' 'gtkglext' 'mesa' 'pangox-compat')
makedepends=('cmake' 'libtool' 'pkgconfig' 'gettext' 'inputproto')
options=('!libtool')
source=(http://launchpad.net/$pkgname-core/3.2/$pkgver/+download/$pkgname-$pkgver.tar.gz)
md5sums=('47a8c9d8981c6f31fae1971a0db1b9a4')

build() {
  cd $srcdir/$pkgname-$pkgver

  [[ -e build ]] || mkdir build 
  cd build
  cmake .. -DCMAKE_INSTALL_PREFIX=/usr
  # put the right path for the themes
  sed -i '6athemesdir=/usr/share/cairo-dock/themes' cairo-dock.pc
  make
}

package() {
  cd $srcdir/$pkgname-$pkgver/build
  make install DESTDIR=$pkgdir
}

