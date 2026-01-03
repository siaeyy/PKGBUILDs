pkgname=instagram-cli
pkgver=1.4.0
pkgrel=1
pkgdesc="Instagram's terminal UI app - The ultimate weapon against brainrot"
arch=('any')
url="https://github.com/supreme-gg-gg/instagram-cli"
license=('MIT')
depends=('node>=20')
source=('https://registry.npmjs.org/@i7m/instagram-cli/-/instagram-cli-1.4.0.tgz')
sha256sums=('e38b98ab331de279459b7245630c785f91ad5c32c683ac1eccb9bca6f2884b1a')

prepare() {
    cd "$srcdir/package"
    npm install
}

package() {
    install -d "$pkgdir/usr/lib/$pkgname"
    mv "$srcdir/package/"* "$pkgdir/usr/lib/$pkgname/"

    cd "$pkgdir/usr/lib/$pkgname"
    mkdir -p "$pkgdir/usr/bin"

    bin="/usr/lib/$pkgname/dist/cli.js"

    ln -s "$bin" "$pkgdir/usr/bin/$pkgname"

    sudo chmod +x "$bin"
    install -Dm644 README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
