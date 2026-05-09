# Maintainer: Ben Brooks <ben@bbrks.me>
# PRs/Issues: https://github.com/bbrks/aur-sync_gateway-community-bin

pkgname=sync_gateway-community-bin
pkgver=4.0.4
pkgrel=1
pkgdesc="Manages access and synchronization between Couchbase Lite and Couchbase Server - Community Edition (CE)"
url="https://github.com/couchbase/sync_gateway"
arch=('x86_64')
license=('custom:Couchbase Community Edition License')
provides=('sync_gateway')
conflicts=('sync_gateway-git')
install="sync_gateway.install"

source=(
	"https://packages.couchbase.com/releases/couchbase-sync-gateway/${pkgver}/couchbase-sync-gateway-community_${pkgver}_x86_64.deb"
	'sync_gateway.service'
)

sha256sums=('411aeeb1b03eebf475202d89a5a5eec3e4e4a5b27e532ea4cc031a3b628d61c3'
            '4bc3c5843b2b6e31d954a53d43c9ecdce77faf3942b5da4ffdaba846f02dd381')

prepare () {
	msg2 "Extracting the data.tar.gz file"
	tar -xf "${srcdir}/data.tar.xz"
}

package() {
	install -Dm755 "${srcdir}/opt/couchbase-sync-gateway/bin/sync_gateway" "${pkgdir}/usr/bin/sync_gateway"
	install -Dm644 "${srcdir}/opt/couchbase-sync-gateway/examples/serviceconfig.json" "${pkgdir}/etc/sync_gateway.json"
	install -Dm644 "${srcdir}/sync_gateway.service" "${pkgdir}/usr/lib/systemd/system/sync_gateway.service"
	install -Dm644 "${srcdir}/opt/couchbase-sync-gateway/LICENSE.txt" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
