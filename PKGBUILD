# Maintainer: Danny <weresocool@xasopheno.com>
pkgname=weresocool
pkgver=1.0.23
pkgrel=1
pkgdesc="***** WereSoCool __!Now In Stereo!__ ****** Make cool sounds. Impress your friends/pets/plants."
url="https://github.com/xasopheno/WereSoCool"
license=("GPL-3.0")
arch=("x86_64")
depends=("portaudio" "pkg-config" "lame" "vorbis-tools")
makedepends=("cargo" "portaudio" "pkg-config" "lame" "vorbis-tools")
provides=("weresocool") 
source=("https://github.com/xasopheno/weresocool/archive/refs/tags/"$pkgver".tar.gz")
shasums=('SKIP')

prepare() {
    cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}

pkgver() {
    (git describe --long --tags || echo "$pkgver") | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cargo build --frozen --release --all-features
}

check() {
    export RUSTUP_TOOLCHAIN=stable
    cargo test --frozen --all-features
}

package() {
    package() {
    install -Dm0755 -t "$pkgdir/usr/bin/" "target/release/$pkgname"
}

