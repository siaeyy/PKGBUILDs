_pkgname=whyis
pkgname="$_pkgname"-git
pkgver=0.0.1
pkgrel=1
pkgdesc="A simple linux troubleshooting utility."
arch=('any')
url="https://github.com/xZepyx/whyis"
license=('MIT')
depends=()
makedepends=('git' 'nim')
source=(git+"$url")
sha256sums=('SKIP')

pkgver() {
    cd "$srcdir/$_pkgname"

    git describe --tags --long | \
        sed 's/^v//;s/-/.r/;s/-/./'
}

build() {
    cd "$srcdir/$_pkgname"

    nim c -d:release whyis.nim
}

package() {
    cd "$srcdir/$_pkgname"

    DATA_DIR="$pkgdir/usr/share/$_pkgname"

    mkdir -p "$DATA_DIR"

    cp symptoms.db "$DATA_DIR/"
    cp -r collectors "$DATA_DIR/"
    cp -r rules "$DATA_DIR/"

    install -Dm755 "$srcdir/$_pkgname/$_pkgname" "$pkgdir/usr/bin/$_pkgname"
    install -Dm644 .github/README.md "$pkgdir/usr/share/doc/$_pkgname/README.md"
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
}
