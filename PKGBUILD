# Maintainer:   Ryo Munakata <afpacket@gmail.com>
# Contributor:  Ryo Munakata <afpacket@gmail.com>
pkgname=mydnsjpd-git
pkgver=r30.b88750d
pkgrel=1
pkgdesc="DNS record updater for MyDNS.jp"
arch=('i686' 'x86_64')
url="https://github.com/pfpacket/mydnsjpd"
license=('GPL2')
depends=('gcc>=4.6.0' 'boost-libs')
makedepends=('boost')
provides=('mydnsjpd')
backup=('etc/mydnsjpd.conf')
install=mydnsjpd.install
source=("$pkgname"::'git://github.com/pfpacket/mydnsjpd.git'
        'mydnsjpd.service')
md5sums=('SKIP'
        '4254c080ec417fd6d15fcf44fb46cfd0')
# Your Boost library path
_boost_root="/usr"

pkgver() {
    cd "$srcdir/$pkgname"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build()
{
    cd "$srcdir/$pkgname"
    make BOOST_ROOT="${_boost_root}"
}

package()
{
    cd "$srcdir/$pkgname"
    install -D -m600 ./mydnsjpd.conf "${pkgdir}/etc/mydnsjpd.conf"
    install -D -m755 ./mydnsjpd "${pkgdir}/usr/bin/mydnsjpd"
    install -D -m644 "${srcdir}/mydnsjpd.service" "${pkgdir}/etc/systemd/system/mydnsjpd.service"
}
