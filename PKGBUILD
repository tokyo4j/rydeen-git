pkgname=rydeen-git
pkgver=r1.ae276ae
pkgrel=1
arch=('x86_64')
pkgdesc='A Linux daemon for keyboard & gesture remapping'
url='https://github.com/tokyo4j/rydeen'
license=('MIT')
depends=('libinput' 'libxkbcommon' 'libevdev' 'libevdev' 'libyaml' 'libev')
makedepends=('meson')
optdepends=()
provides=('rydeen')
conflicts=('rydeen')
source=("${pkgname}::git+https://github.com/tokyo4j/rydeen")
sha256sums=('SKIP')
backup=('etc/rydeen/config.yml')

pkgver() {
	cd "${srcdir}/${pkgname}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "${srcdir}/${pkgname}"
	meson setup --buildtype=release release
    meson compile -C release
}

package() {
	cd "${srcdir}/${pkgname}"
    meson install -C release --destdir=${pkgdir}
}
