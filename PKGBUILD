# Maintainer: George Raven <GeorgeRavenCommunity AT outlook dot com>
pkgname=python-pimoroni-bme680-git
pkgsrcname="bme680-python"

pkgver=0.0.0

pkgrel=1
pkgdesc="Python library for the BME680 gas, temperature, humidity, and pressure sensor."
arch=('any')
# pimoroni bme680 python source code url
url="https://github.com/DreamingRaven/bme680-python"
# set what branch you would like to pull from
branch="master"
license=('MIT') # MIT is a special case store a copy in /usr/share/pkgname
groups=()
depends=("python")
makedepends=("git") # 'bzr', 'git', 'mercurial' or 'subversion'
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
source=("${pkgsrcname}::git+https://github.com/pimoroni/${pkgsrcname}#branch=${branch}")
noextract=()
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgsrcname}"
	printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"
}

prepare() {
	cd "$srcdir/${pkgsrcname}"
	git checkout ${branch} # get off of makepkg branch
}

build() {
	cd "$srcdir/${pkgsrcname}"
}

check() {
	cd "$srcdir/${pkgsrcname}"
}

package() {
	cd "$srcdir/${pkgsrcname}/library" # they store their setup.py here
	python3 setup.py install --prefix=/usr --root="$pkgdir/" --optimize=1
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
