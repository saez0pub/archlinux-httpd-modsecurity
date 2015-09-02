# Maintainer: Somebody <somebody[at]foo[dot]tld>
pkgname=apache-modsecurity
pkgver=2.9.0
pkgrel=1
pkgdesc="mod_security for apache."
url="http://www.modsecurity.org/"
arch=('any')
license=('ASLv2')
depends=('apr' 'apr-util' 'libxml2' 'curl' 'lua51' 'pcre')
makedepends=()
source=("https://www.modsecurity.org/tarball/2.9.0/modsecurity-${pkgver}.tar.gz")
md5sums=('ecf42d21f26338443d7111891851628c')

package() {
  cd "${srcdir}/modsecurity-${pkgver}"
  ./configure --prefix=/opt/modsecurity/ --with-lua=/usr/include/lua5.1/
  make DESTDIR="${pkgdir}" install
}

