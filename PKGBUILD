# Maintainer and Author: Ehsan Ghorbannezhad <ehsan at disroot dot org>
pkgname=pkgsync-local
pkgdesc='Sync package cache between LAN devices using rsync'
pkgver=r2
pkgrel=1
arch=(any)
license=(GPL)
depends=(rsync avahi)
makedepends=(gettext)
source=(pkgsync pkgsync-daemon pkgsync.runit pkgsync.hook rsyncd.conf.env auth)
backup=(etc/pkgsync/rsyncd.conf etc/pkgsync/auth)
md5sums=(SKIP SKIP SKIP SKIP SKIP SKIP)

build() {
    ARCH=$(uname -m) envsubst < rsyncd.conf.env > rsyncd.conf
}

package() {
    install -Dm755 pkgsync pkgsync-daemon -t "$pkgdir"/usr/bin/
    install -Dm755 pkgsync.runit "$pkgdir"/etc/runit/sv/pkgsync/run
    install -Dm644 pkgsync.hook -t "$pkgdir"/usr/share/libalpm/hooks/
    install -Dm644 rsyncd.conf -t "$pkgdir"/etc/pkgsync/
    install -Dm600 auth -t "$pkgdir"/etc/pkgsync/
}
