# $Id$
# Maintainer:  Ionut Biru <ibiru@archlinux.org>
# Contributor: Ju Liu <liuju86 at gmail dot com>
# Contributor: Bjorn Lindeijer <bjorn lindeijer nl>
# Contributor: Andreas Zwinkau <beza1e1@web.de>

pkgname=telepathy-mission-control-uoa
_pkgname=telepathy-mission-control
pkgver=5.14.1
pkgrel=1
pkgdesc="A Telepathy component providing abstraction of some of the details of connection managers."
arch=('i686' 'x86_64')
url="http://telepathy.freedesktop.org/wiki/Mission Control"
license=('LGPL2.1')
depends=('telepathy-glib' 'libgnome-keyring' 'dconf' 'upower' 'networkmanager')
makedepends=('libxslt' 'python2')
conflicts=('telepathy-mission-control')
replaces=('telepathy-mission-control')
provides=('telepathy-mission-control')
install=telepathy-mission-control.install
options=('!libtool')
source=("http://telepathy.freedesktop.org/releases/$_pkgname/$_pkgname-$pkgver.tar.gz" 'uoa.patch')
md5sums=('e06fb0399ec435e59c74d79a2ace8a2d' 'e6edd5e0cf632fccfaa77d8493c7bc2a')

build() {
    cd "$_pkgname-$pkgver"
    patch -Np1 -i ../uoa.patch
    PYTHON=python2 ./configure --prefix=/usr \
    	--libexecdir=/usr/lib/telepathy \
	--enable-gnome-keyring \
        --disable-schemas-compile
    make
}

package() {
    cd "$_pkgname-$pkgver"
    make DESTDIR="$pkgdir" install
}
