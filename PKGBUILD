# Maintainer: Alucryd <alucryd at gmail dot com>

pkgname=vala0.19
pkgver=0.19.0
pkgrel=2
pkgdesc="Compiler for the GObject type system - 0.19 version"
arch=('i686' 'x86_64')
url="http://live.gnome.org/Vala"
license=('LGPL')
depends=('bash' 'glib2')
makedepends=('libxslt')
provides=("vala=${pkgver}")
options=('!libtool')
source=("http://download.gnome.org/sources/${pkgname%0.19}/0.19/${pkgname%0.19}-${pkgver}.tar.xz")
sha256sums=('7781c8cb5416c10ba53ccf6b216966ba864fee71bb26d23ffaef29cb2011c5ee')

build() {
  cd "${srcdir}"/${pkgname%0.19}-${pkgver}

# Build
  ./configure --prefix=/usr --enable-vapigen
  make
}

package() {
  cd "${srcdir}"/${pkgname%0.19}-${pkgver}

# Install
  make DESTDIR="${pkgdir}" install

# Prevent conflicts
  rm -rf "${pkgdir}"/usr/{bin/{vala,valac,vala-gen-introspect,vapicheck,vapigen},share/{man/man1/{valac.1,vala-gen-introspect.1,vapigen.1},pkgconfig/vapigen.pc,vala}}
  mv "${pkgdir}"/usr/share/aclocal/vala.m4 "${pkgdir}"/usr/share/aclocal/vala-0.20.m4
  mv "${pkgdir}"/usr/share/aclocal/vapigen.m4 "${pkgdir}"/usr/share/aclocal/vapigen-0.20.m4
}

# vim:set ts=2 sw=2 et:
