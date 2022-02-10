# Maintainer and Author: Ehsan Ghorbannezhad <ehsan at disroot dot org>
pkgname=pacrsync-local
pkgdesc='Sync package cache between LAN devices using rsync'
pkgver=1
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

sha256sums=('f7fc6a5eb2c0a9f8e4ada257b597db329bccc679b9d7f09c24f6cf0a1a4ce4cc'
            '4772152ac21cb7ec5c83e0810c0c3fa227eb243195e472d6310ea2065192e6d0'
            '0e00cb573d63513beb3eb1e50f112a5766d9fb01f1355c35b4f1f36a9c257126'
            'a4fd4b7131d9b69e8033c8fa342ccb05f42034b7b34df7a8856dd7d78a40892d'
            'd2a09f2c4100cb1b5a80fd5086bf9c99dd0f6079bc4427252532237105014ff4')
