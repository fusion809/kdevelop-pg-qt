# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kdevelop-pg-qt
pkgver=2.0.0
pkgrel=1
pkgdesc="KDevelop Parser Generator, a LL(1) parser generator used by KDevelop language plugins. (GIT version)"
arch=('i686' 'x86_64')
url='http://www.kdevelop.org'
license=('GPL')
depends=('qt5-base')
makedepends=('cmake' 'git' 'extra-cmake-modules')
source=("git://anongit.kde.org/kdevelop-pg-qt.git#tag=v${pkgver}")
sha1sums=('SKIP')

pkgver() {
  cd "${srcdir}/${pkgname}"
  git describe --tags `git rev-list --tags --max-count=1` | sed 's/v//g'
}

prepare() {
  if [[ -d build ]]; then
    rm -rf build
  fi
  mkdir build
}

build() {
  cd build
  cmake ../kdevelop-pg-qt \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DBUILD_TESTING=OFF
  make
}

package() {
  make -C build DESTDIR="${pkgdir}" install
}
