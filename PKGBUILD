# Maintainer: Maxime Morel <maxime@mmorel.eu>

pkgname=dali-adaptor-git
pkgver=1.0.41
pkgrel=1
pkgdesc="OpenGl based 3D GUI toolkit - adaptor"
arch=('x86_64' 'i686')
url="git://git.tizen.org/platform/core/uifw/dali-adaptor"
license=('APACHE')
depends=('dali-core-git' 'elementary' 'boost-libs' 'libexif')
makedepends=('git' 'autoconf' 'boost')
provides=('dali-adaptor')
conflicts=('dali-adaptor')
source=("git://git.tizen.org/platform/core/uifw/dali-adaptor" "0001-fix.patch")
md5sums=('SKIP' 'b43531e9a1f1e35efd13c0f916d9de87')

pkgver() {
  cd "$srcdir/dali-adaptor"
  printf "%s" "$(git describe | sed -r 's/^dali_(.*)-[0-9]+-[a-z0-9]+$/\1/')"
}

prepare() {
  cd "$srcdir/dali-adaptor"
  patch -p1 < ../0001-fix.patch
}

build() {
  cd "$srcdir/dali-adaptor/build/tizen"
  autoreconf --install
  ./configure --help
  ./configure --prefix=/usr --enable-profile=UBUNTU --enable-gles=20
  make CXXFLAGS=-Wno-error
}

package() {
  cd "$srcdir/dali-adaptor/build/tizen"
  make DESTDIR="$pkgdir/" install
}

