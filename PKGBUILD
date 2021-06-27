# Maintainer: Aru Sahni <aru@arusahni.net>
pkgname=git-req
pkgver=2.4.0
pkgrel=1
epoch=
pkgdesc="Switch between merge/pull requests in your GitLab and GitHub repositories with just the request ID."
arch=('x86_64')
url="https://arusahni.github.io/git-req/"
license=('MIT')
groups=()
depends=('git')
makedepends=('cargo')
checkdepends=()
optdepends=()
provides=('git-req')
conflicts=('git-req')
replaces=()
backup=()
options=()
install=
changelog=
source=("$pkgname-$pkgver.tar.gz::https://github.com/arusahni/$pkgname/archive/v$pkgver.tar.gz")
noextract=()
sha256sums=('fcce9bbea6c2c888b115aee4db274263582b8eb472da079b281ee89dbee35a4f')
validpgpkeys=()

build() {
    cd "$pkgname-$pkgver"
    cargo build --release --locked
}

check() {
    cd "$pkgname-$pkgver"
    cargo test --locked
}

package() {
    cd "$pkgname-$pkgver"
    cargo install --root "${pkgdir}"/usr --path "${srcdir}/${pkgname}-${pkgver}"
    install -D -m644 "${srcdir}/${pkgname}-${pkgver}/target/release/${pkgname}.1" "${pkgdir}/usr/share/man/man1/${pkgname}.1"
    # Random metadata file created by cargo. See https://github.com/rust-lang/cargo/issues/6797
    rm "${pkgdir}"/usr/.crates.toml
}
