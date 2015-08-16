# Maintainer: Padfoot <padfoot at exemail dot com dot au>

pkgname=lightdm-gtk-greeter-osk
_srcname=lightdm-gtk-greeter
pkgver=1.5.0
pkgrel=2
pkgdesc="GTK+ greeter for LightDM with on-screen keyboard support"
arch=('i686'
      'x86_64')
url="https://launchpad.net/lightdm-gtk-greeter"
license=('GPL3'
         'LGPL3')
depends=('lightdm'
         'gtk3')
makedepends=('gtk-doc'
             'gnome-common'
             'gnome-doc-utils'
             'gobject-introspection'
             'intltool'
             'patch')
provides=('lightdm-gtk-greeter')
conflicts=('lightdm-gtk-greeter'
           'lightdm-gtk-greeter-bzr')
backup=('etc/lightdm/lightdm-gtk-greeter.conf')
install='lightdm-gtk-greeter.install'
source=("https://launchpad.net/$_srcname/1.6/$pkgver/+download/$_srcname-$pkgver.tar.gz"
        "lightdm-gtk-greeter.conf"
        "lightdm-gtk-greeter.patch")
md5sums=('226fbc12594cca01d5decabde1d42f2d'
         '9a2359364c9af0216516b6330f2ff7f8'
         'b5fd47d966ec49698b8f362c039d408d')

build() {
  cd "$srcdir/$_srcname-$pkgver"

  patch -p1 -i $srcdir/lightdm-gtk-greeter.patch
  
  export AUTOMAKE=automake
  ./autogen.sh --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib/lightdm \
    --disable-static
    
  make
}

package() {
  cd "$srcdir/$_srcname-$pkgver"
  
  make DESTDIR="${pkgdir}" install

  cp ../lightdm-gtk-greeter.conf $pkgdir/etc/lightdm
}
