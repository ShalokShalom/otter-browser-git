#Maintainer:

_pkgname=otter
pkgname=${_pkgname}-browser-git
pkgver=0.9.01.r14
pkgrel=1
pkgdesc='Otter Browser, project aiming to recreate classic Opera (12.x) using Qt5.'
arch=('x86_64')
url="http://www.otter-browser.org"
license=('Unknown')
depends=('qt5-base' 'qt5-webkit')
makedepends=('qt5-base' 'qt5-webkit' 'git')
source=("git://github.com/emdek/${_pkgname}.git")
md5sums=('SKIP')

pkgver() {
	cd "${srcdir}/${_pkgname}"
	if GITTAG="$(git describe --abbrev=0 --tags 2>/dev/null)"; then
		echo "$(sed -e 's/^[-_/a-zA-Z]\+//' -e 's/[-_+]/./g' <<< ${GITTAG}).r$(git rev-list --count ${GITTAG}..)"
	else
		echo "0.r$(git rev-list --count master)"
	fi
}

build() {
	cd "${srcdir}/${_pkgname}"
	mkdir build
	cd build
	cmake -DCMAKE_INSTALL_PREFIX=/usr ..
	make
}

package() {
	cd "${srcdir}/${_pkgname}"

	install -Dm644 "COPYING" "${pkgdir}/usr/share/licences/${_pkgname}-browser/LICENSE"
	install -Dm644 "${_pkgname}-browser.desktop" "${pkgdir}/usr/share/applications/${_pkgname}-browser.desktop"

	cd "build"
	make DESTDIR=${pkgdir} install
}
