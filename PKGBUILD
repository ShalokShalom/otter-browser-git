
_pkgname=otter
pkgname=${_pkgname}-browser-git
pkgver=706
pkgrel=1
pkgdesc='Otter Browser, project aiming to recreate classic Opera (12.x) using Qt5.'
arch=('x86_64')
url="http://www.otter-browser.org"
license=('Unknown')
depends=('qt5-base' 'qt5-webkit' 'qt5-script')
makedepends=('git')
source=("git://github.com/emdek/${_pkgname}.git")
md5sums=('SKIP')

pkgver() {
	cd "${srcdir}/${_pkgname}"
	git rev-list --count HEAD
}

build() {
	cd "${srcdir}/${_pkgname}"
	mkdir build
	cd build
	qmake-qt5 ../otter.pro
	make
}

package() {
	install -dm755 ${pkgdir}/usr/{share/applications,bin}
	mv "${srcdir}/${_pkgname}/build/${_pkgname}-browser" "${pkgdir}/usr/bin/${_pkgname}-browser"
	mv "${srcdir}/${_pkgname}/${_pkgname}-browser.desktop" "${pkgdir}/usr/share/applications/${_pkgname}-browser.desktop"
}
