# Maintainer and Author: Ehsan Ghorbannezhad <ehsan at disroot dot org>
pkgname=pkgsync-local
pkgdesc='Sync package cache between LAN devices using rsync'
pkgver=r1
pkgrel=1
arch=(any)
license=(GPL)
depends=(rsync avahi)
makedepends=(gettext)
source=(pkgsync pkgsync-daemon pkgsync.runit pkgsync.hook rsyncd.conf.env auth)
backup=(etc/pkgsync/rsyncd.conf etc/pkgsync/auth)

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

sha256sums=('73eb900930f770f752186ec80f87e6262b56fcea4c45861d6c3c57ae11f7ac1f'
            'add17d8184e477b7e084df1f7b9fc799ead1af21e3c62df5ca5e0645144d62f0'
            'a0aecdbaf9ca50f33c4327bfc45b46810a1d568fbd7f47ccc2d220293867d1e3'
            '12140544b553e53dc742f893ddda3e7fab1b0cc97c16dbe844bad9f602d5e020'
            '4aaaa6c48babb0666963ef693a7dde32752262ce02fce2a3e86810ec09cdbff8'
            'd55d9ef8a15f59408ccceabc974199bfb02b8885132d2f4364b98b0f7955afed')
