#!/usr/bin/env bash
# Maintainer: Gino Gravanis

pkgname=dwm
pkgver=1
pkgrel=1
pkgdesc='Dynamic window manager for X'
arch=('i686' 'x86_64')
url='https://dwm.suckless.org/'
license=('MIT')
depends=()
makedepends=('git')
provides=()
conflicts=()
source=(
   'git+https://git.suckless.org/dwm'
   'https://dwm.suckless.org/patches/centeredmaster/dwm-centeredmaster-20160719-56a31dc.diff'
)
extra_patches=(
   'font-size.diff'
   'key-bindings.diff'
)
md5sums=(
   'SKIP'
   '0051114992d940bc2ce1ed9ddcdcd8f8'
)

prepare() {
   local srcroot="$srcdir/$pkgname"
   for patch in "${source[@]:1}" "${extra_patches[@]}"; do
      patch -d "$srcroot" -p1 -i "$BUILDDIR/$(basename "$patch")"
   done
   cp "$srcroot/config.def.h" "$srcroot/config.h"
}

pkgver() {
   git -C "$srcdir/$pkgname" describe --long --tags | sed 's/-/./g'
}

build() {
   make -C "$srcdir/$pkgname"
}

package() {
   local srcroot="$srcdir/$pkgname"
   local license_dir="$pkgdir/usr/share/licenses/$pkgname"
   make -C "$srcdir/$pkgname" PREFIX=/usr DESTDIR="$pkgdir/" install
   install -Dm644 "$srcroot/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
   install -Dm644 "$srcroot/README" "$pkgdir/usr/share/doc/$pkgname/README"
}
