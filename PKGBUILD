# Maintainer: Wang Jiajun <amesists@gmail.com>
pkgname=kdesrc-build
pkgver=1.15.1
pkgrel=1
pkgdesc="A tool to allow you to easily build KDE from its source repositories."
url="http://kdesrc-build.kde.org/"
arch=('any')
license=('GPL')
depends=('perl' 'perl-libwww' 'perl-xml-parser' 'dialog' 'perl-json')
makedepends=('cmake')
optdepends=('subversion: download source code using svn'
            'git: download source code using git')
source=("http://download.kde.org/stable/${pkgname}/${pkgver}/src/${pkgname}-${pkgver}.tar.xz")
md5sums=('9469a5fcc585e0f37cc295b44a0d36e1')

build() {
  cd "${srcdir}"
  mkdir build
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
  make
}

package() {
  cd "${srcdir}"/build
  make DESTDIR="${pkgdir}" install

  mkdir -p "${pkgdir}/usr/share/kdesrc-build/"
  cp "${srcdir}/${pkgname}-${pkgver}/kdesrc-buildrc-sample" "${pkgdir}/usr/share/kdesrc-build/"
}
