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

sha256sums=('e9f03250b56575227d4e3a6595faae249981aaa4ef99da329968865c86e41034'
            'add17d8184e477b7e084df1f7b9fc799ead1af21e3c62df5ca5e0645144d62f0'
            'a0aecdbaf9ca50f33c4327bfc45b46810a1d568fbd7f47ccc2d220293867d1e3'
            '12140544b553e53dc742f893ddda3e7fab1b0cc97c16dbe844bad9f602d5e020'
            '90931d60ba34abc30af5d6bb18496e33d1cb95ae21b44e7d566ddbdddc9db704'
            'd55d9ef8a15f59408ccceabc974199bfb02b8885132d2f4364b98b0f7955afed')
