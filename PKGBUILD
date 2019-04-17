# Maintainer: Alexey Pavlov <alexpux@gmail.com>

_realname=libsodium
pkgbase=${_realname}
pkgname="${_realname}"
pkgver=1.0.17
pkgrel=1
pkgdesc="P(ortable|ackageable) NaCl-based crypto library"
arch=("any")
url="https://github.com/jedisct1/libsodium"
license=('custom:ISC')
depends=("gcc-libs")
source=("https://download.libsodium.org/libsodium/releases/${_realname}-${pkgver}.tar.gz")
sha256sums=('0cc3dae33e642cc187b5ceb467e0ad0e1b51dcba577de1190e9ffa17766ac2b1')

build() {
  rm -rf "${srcdir}/build"
  mkdir "${srcdir}/build"
  cd "${srcdir}/build"

  ../${_realname}-${pkgver}/configure \
    --enable-shared \
    --enable-static

  make
}

check() {
  cd build
  make -k check
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
  install -Dm644 ${srcdir}/${_realname}-${pkgver}/LICENSE "${pkgdir}/share/licenses/${_realname}/LICENSE"
}
