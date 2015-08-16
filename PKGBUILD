# Maintainer: josephgbr <rafael.f.f1@gmail.com>

_pkgbase=lcms2
pkgname=lib32-${_pkgbase}
pkgver=2.5
pkgrel=1
pkgdesc="Small-footprint color management engine, version 2 (32 bit)"
arch=('x86_64')
license=('MIT')
depends=('lib32-glibc' "${_pkgbase}") # 'libtiff>=3.9.4'
makedepends=('gcc-multilib')
url="http://www.littlecms.com"
options=('!libtool')
source=(http://downloads.sourceforge.net/sourceforge/lcms/${_pkgbase}-${pkgver}.tar.gz)
sha1sums=('bab3470471fc7756c5fbe71be9a3c7d677d2ee7b')

build() {
  export CC='gcc -m32'
  
  cd ${_pkgbase}-${pkgver}
  ./configure --prefix=/usr --libdir=/usr/lib32 \
  	--without-jpeg --without-tiff
  make
}

package() {
  make -C ${_pkgbase}-${pkgver} DESTDIR="${pkgdir}" install
  rm -rf "${pkgdir}"/usr/{bin,include,share}
  
  install -dm755 "${pkgdir}"/usr/share/licenses
  ln -s ${_pkgbase} "${pkgdir}"/usr/share/licenses/${pkgname}
}
