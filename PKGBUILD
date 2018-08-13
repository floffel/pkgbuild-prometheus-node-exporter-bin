# Maintainer: Slashbunny <demodevil5[at]yahoo>

pkgname=prometheus-node-exporter-bin
pkgver=0.16
pkgrel=1
pkgdesc="Prometheus exporter for machine metrics (binary, not built from source)"
arch=('x86_64' 'armv7h')
url="https://github.com/prometheus/node_exporter"
license=('Apache')
depends=()
makedepends=()
provides=('prometheus-node-exporter')
conflicts=('prometheus-node-exporter')
source_x86_64=( 'prometheus-node-exporter.service'
"https://github.com/prometheus/node_exporter/releases/download/v${pkgver}/node_exporter-${pkgver}.linux-amd64.tar.gz")
source_armv7h=( 'prometheus-node-exporter.service'
"https://github.com/prometheus/node_exporter/releases/download/v${pkgver}/node_exporter-${pkgver}.linux-armv7.tar.gz")
sha256sums_x86_64=('SKIP'
                   'SKIP')
sha256sums_armv7h=('SKIP'
                   'SKIP')

package() {
    case "$CARCH" in
            'x86_64') ARCH='amd64';;
            'armv7h') ARCH='armv7';;
    esac
    cd "${srcdir}/node_exporter-${pkgver}.linux-${ARCH}"

    # Install Binary
    install -D -m0755 node_exporter \
        "${pkgdir}/usr/bin/prometheus_node_exporter"

    # Install SystemD Service File
    install -D -m0644 "${srcdir}/prometheus-node-exporter.service" \
        "${pkgdir}/usr/lib/systemd/system/prometheus-node-exporter.service"
}
