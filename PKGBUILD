# Maintainer: Allan McRae <mcrae_allan@hotmail.com>
# Contributor: Briquet <mb_briquet@yahoo.es>

pkgname=gtvg
pkgver=0.3
pkgrel=3
pkgdesc="A simple TV program schedule viewer"
arch=('i686' 'x86_64')
url="http://gtvg.sourceforge.net/index.html"
license=('GPL')
depends=('libnotify' 'libgnomecanvas' 'libgnome')
makedepends=('intltool')
install=gtvg.install
source=(http://downloads.sourceforge.net/gtvg/$pkgname-$pkgver.tar.gz)
md5sums=('6e3dd67f7f98a3217e4a960fb2eb5466')

build() {
  cd ${srcdir}/$pkgname-$pkgver

  ./configure --prefix=/usr --sysconfdir=/etc
  make || return 1
  make DESTDIR=${pkgdir} install || return 1

  install -dm755 ${pkgdir}/usr/share/gconf/schemas
  gconf-merge-schema ${pkgdir}/usr/share/gconf/schemas/${pkgname}.schemas \
    ${startdir}/pkg/etc/gconf/schemas/*.schemas
  rm -rf ${pkgdir}/etc/
}
