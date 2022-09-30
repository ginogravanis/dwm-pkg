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
source=('git+https://github.com/ginogravanis/dwm.git')
md5sums=('SKIP')

pkgver() {
   git -C "$srcdir/$pkgname" describe --long --tags | sed 's/-/./g'
}

build() {
   make -C "$srcdir/$pkgname"
}

package() {
   local srcroot="$srcdir/$pkgname"
   make -C "$srcdir/$pkgname" PREFIX=/usr DESTDIR="$pkgdir/" install
   install -Dm644 "$srcroot/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
   install -Dm644 "$srcroot/README" "$pkgdir/usr/share/doc/$pkgname/README"
}
