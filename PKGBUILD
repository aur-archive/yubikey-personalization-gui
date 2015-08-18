# Maintainer: Christian Hesse <mail@eworm.de>

pkgname=yubikey-personalization-gui
pkgver=3.1.21
pkgrel=1
pkgdesc='Yubico YubiKey Personalization GUI'
arch=('i686' 'x86_64')
url='https://github.com/Yubico/yubikey-personalization-gui'
license=('BSD')
depends=('yubikey-personalization' 'qt5-base' 'libxkbcommon-x11')
makedepends=('git' 'imagemagick')
provides=('yubikey-personalization-tool')
conflicts=('yubikey-personalization-tool' 'yubikey-personalization-gui-git')
install=yubikey-personalization-gui.install
source=("git://github.com/Yubico/yubikey-personalization-gui.git#tag=yubikey-personalization-gui-${pkgver}")
sha256sums=('SKIP')

build() {
	cd yubikey-personalization-gui/

	qmake-qt5 "CONFIG += debian"
	make
}

check() {
	cd yubikey-personalization-gui/

	make check
}

package() {
	cd yubikey-personalization-gui/

	install -D -m0755 build/release/yubikey-personalization-gui "${pkgdir}/usr/bin/yubikey-personalization-gui"
	install -D -m0644 resources/lin/yubikey-personalization-gui.1 "${pkgdir}/usr/share/man/man1/yubikey-personalization-gui.1"

	install -D -m0644 resources/lin/yubikey-personalization-gui.desktop "${pkgdir}/usr/share/applications/yubikey-personalization-gui.desktop"

	install -D -m0644 resources/lin/yubikey-personalization-gui.png "${pkgdir}/usr/share/icons/hicolor/128x128/apps/yubikey-personalization-gui.png"
	for SIZE in 16 24 32 48 64 96; do
		convert -scale ${SIZE} \
			resources/lin/yubikey-personalization-gui.png \
			${srcdir}/yubikey-personalization-gui.png
		install -D -m0644 ${srcdir}/yubikey-personalization-gui.png "${pkgdir}/usr/share/icons/hicolor/${SIZE}x${SIZE}/apps/yubikey-personalization-gui.png"
	done

	install -D -m0644 COPYING "${pkgdir}/usr/share/licenses/yubikey-personalization-gui/COPYING"
	install -D -m0644 README "${pkgdir}/usr/share/doc/yubikey-personalization-gui/README"
}

