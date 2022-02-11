# Maintainer and Author: Ehsan Ghorbannezhad <ehsan at disroot dot org>
pkgname=pacrsync-local
pkgdesc='Sync package cache between LAN devices using rsync'
pkgver=2
pkgrel=1
arch=(any)
license=(GPL)
depends=(rsync avahi)
makedepends=(gettext)
source=(pacrsync pacrsync.hook pacrsync.runit rsyncd.conf.env rsyncd.secrets)

build() {
    ARCH=$(uname -m) envsubst < rsyncd.conf.env > rsyncd.conf
}

package() {
    install -Dm755 pacrsync -t "$pkgdir"/usr/bin/
    install -Dm755 pacrsync.runit "$pkgdir"/etc/runit/sv/pacrsync/run
    install -Dm644 pacrsync.hook -t "$pkgdir"/usr/share/libalpm/hooks/
    install -Dm644 rsyncd.conf -t "$pkgdir"/etc/pacrsync/
    install -Dm600 rsyncd.secrets -t "$pkgdir"/etc/pacrsync/
}

sha256sums=('71a9bf52b04fc9d5cb9e23b46e5b0c487bb3b5c3a40fe19bf0a433160a22f1e0'
            '4772152ac21cb7ec5c83e0810c0c3fa227eb243195e472d6310ea2065192e6d0'
            '49c478da48a6fa805f92a9e5456c36969d8496574cba6e6d04c81461eea8da1e'
            '547dc09bf0c82e6fafad967b4238bb6a0eeaf3fa9756afad6e30a72deb03a736'
            'd2a09f2c4100cb1b5a80fd5086bf9c99dd0f6079bc4427252532237105014ff4')
