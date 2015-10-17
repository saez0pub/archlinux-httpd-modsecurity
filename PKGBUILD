# Maintainer: saez0pub https://github.com/saez0pub/archlinux-modsecurity.git
pkgname=apache-modsecurity
pkgver=2.9.0
pkgrel=1
pkgdesc="mod_security for apache."
url="http://www.modsecurity.org/"
arch=('any')
license=('ASLv2')
depends=('apr' 'apr-util' 'libxml2' 'curl' 'lua51' 'pcre')
makedepends=()
source=("https://www.modsecurity.org/tarball/2.9.0/modsecurity-${pkgver}.tar.gz"
	'modsecurity-apache.conf')
md5sums=('ecf42d21f26338443d7111891851628c'
	'ea01299d9706ddb2742b928877679f92')

package() {
  cd "${srcdir}/modsecurity-${pkgver}"
  ./configure --prefix=/opt/modsecurity/ --with-lua=/usr/include/lua5.1/
  make DESTDIR="${pkgdir}" install
  mkdir -p ${pkgdir}/opt/modsecurity/{bin,etc,var,var/audit,var/data,var/log,var/tmp,var/upload}
  install -D -m700 ${srcdir}/modsecurity.conf ${pkgdir}/opt/modsecurity/etc
  chown root:http ${pkgdir}/opt/modsecurity/{,bin,var}
  chown http:http ${pkgdir}/opt/modsecurity/var/tmp
  chown http:root ${pkgdir}/opt/modsecurity/{var/audit,var/data,var/upload}
  chown root:root ${pkgdir}/opt/modsecurity/{etc,var/log}
  touch ${pkgdir}/opt/modsecurity/etc/{main.conf,rules-first.conf,rules.conf,rules-last.conf}
  chmod 750 ${pkgdir}/opt/modsecurity/{,bin,var,var/tmp}
  chmod 700 ${pkgdir}/opt/modsecurity/{etc,etc/*,var/audit,var/data,var/log,var/upload}
}

