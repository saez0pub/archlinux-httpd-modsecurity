# Maintainer: saez0pub https://github.com/saez0pub/archlinux-httpd-modsecurity.git
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
  mkdir -p ${pkgdir}/opt/modsecurity/{bin,etc,var,var/audit,var/data,var/log,var/tmp,var/upload}
  chown root:http ${pkgdir}/opt/modsecurity/{,bin,var}
  chown http:http ${pkgdir}/opt/modsecurity/var/tmp
  chown http:root ${pkgdir}/opt/modsecurity/{var/audit,var/data,var/upload}
  chown root:root ${pkgdir}/opt/modsecurity/var/log
  chmod 750 ${pkgdir}/opt/modsecurity/{,bin,var,var/tmp}
  chmod 700 ${pkgdir}/opt/modsecurity/{etc,var/audit,var/data,var/log,var/upload}
}

