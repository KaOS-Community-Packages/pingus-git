pkgname=pingus-git
_pkgname=pingus
pkgver=0.7.6.r431.g5b9ffa9fb
pkgrel=1
pkgdesc="A Lemmings clone, i.e. a level-based puzzle game."
arch=('x86_64')
url="http://pingus.gitlab.io"
license=('GPL')
depends=('sdl2_image' 'sdl2_mixer' 'libglvnd' 'boost-libs>=1.49')
makedepends=('git' 'cmake' 'boost>=1.49' 'mesa' 'glu')
conflicts=('pingus')
source=("$_pkgname-$pkgver::git+https://gitlab.com/$_pkgname/$_pkgname.git#branch=master")
md5sums=('SKIP')

pkgver(){
	cd $srcdir/$_pkgname-$pkgver
	git describe --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare(){
	cd $srcdir/$_pkgname-$pkgver
	git submodule update --init --recursive
}

build() {
	mkdir -p $srcdir/$_pkgname-$pkgver/build && cd $srcdir/$_pkgname-$pkgver/build
	cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr
}

package() {
  cd $srcdir/${_pkgname}-${pkgver}/build

  make install DESTDIR="${pkgdir}"
}
