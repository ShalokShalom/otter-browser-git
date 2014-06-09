
pkgname=otter-browser-git
_pkgname=otter
pkgver=894
pkgrel=1
pkgdesc='Otter Browser, project aiming to recreate classic Opera (12.x) using Qt5.'
arch=('x86_64')
url="http://www.otter-browser.org"
license=('GPL3')
depends=('qt5-base' 'qt5-webkit' 'qt5-script' 'desktop-file-utils' 'hicolor-icon-theme')
makedepends=('git' 'cmake' 'qt5-tools')
source=("git://github.com/emdek/${_pkgname}.git")
md5sums=('SKIP')

pkgver() {
   cd "${srcdir}/${_pkgname}"
   git rev-list --count HEAD
}

build() {
   cd "${srcdir}/${_pkgname}"
   /usr/lib/qt5/bin/lrelease resources/translations/*.ts
	
   mkdir build
   cd build
   cmake -DCMAKE_INSTALL_PREFIX="/usr" ../
   make
}

package() {
   cd "${srcdir}/${_pkgname}"/build	
   make DESTDIR=${pkgdir} install
	
   install -D -m0644 "${srcdir}/${_pkgname}"/COPYING \
        ${pkgdir}/usr/share/licenses/otter-browser/COPYING
}
