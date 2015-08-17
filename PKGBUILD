# Maintainer: acounto <acounto at kamikakushi dot net>

pkgname=recpt1
pkgver=133
_foldername=pt1-b14397800eae
pkgrel=2
pkgdesc="ISDB-T/S Recording Program for PT1/2/3"
arch=('i686' 'x86_64')
url='http://hg.honeyplanet.jp/pt1'
license=('unknown')
depends=('libarib25' 'pcsclite')
conflicts=('recpt1-stz')
optdepends=('pt3-drv: PT3 chardev driver')
source=('http://hg.honeyplanet.jp/pt1/archive/b14397800eae.tar.bz2' 'recpt1_all.diff' 'decorder.h_typo.diff' 'pt1_dev.h.diff')
md5sums=('d4a775c5c084ab848b823bc448bb3dd2' '8fd98dfb0c4b8630a8edbe088d660068' 'd89e33cbee48dbe6fb1bb2433059f29f' '7bcbf17c5506b0ec06bfabdd463382bf')

build() {
  patch -p0 -i $srcdir/recpt1_all.diff
  patch -p0 -i $srcdir/decorder.h_typo.diff
  patch -p0 -i $srcdir/pt1_dev.h.diff
  cd $srcdir/$_foldername/recpt1
  ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/etc --datadir=/usr/share --enable-b25 
  make
}

package() {
  cd $srcdir/$_foldername/recpt1
  mkdir -p "${pkgdir}/usr/bin"
  make DESTDIR="${pkgdir}" install
}
