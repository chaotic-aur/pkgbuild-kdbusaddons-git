# Merged with official ABS kdbusaddons PKGBUILD by João, 2021/02/01 (all respective contributors apply herein)
# Maintainer: João Figueiredo & chaotic-aur <islandc0der@chaotic.cx>
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kdbusaddons-git
pkgver=5.83.0_r362.g5cc8df6
pkgrel=1
pkgdesc='Addons to QtDBus'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
depends=(qt5-x11extras)
makedepends=(git extra-cmake-modules-git qt5-tools clang python-pyqt5 doxygen sip4)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('python-pyqt5: for the Python bindings')
groups=(kf5-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}