# Maintainer: Aditya Shakya <adi1090x@gmail.com>

pkgname=archcraft-evilwm
pkgver=1.0
pkgrel=0
pkgdesc="EvilWM Configurations for Archcraft"
url="https://github.com/archcraft-os/archcraft-evilwm"
arch=('any')
license=('GPL3')
makedepends=('git')
depends=('evilwm' 'xorg-fonts-100dpi' 'xorg-fonts-75dpi' 'xorg-font-util'
		'xorg-fonts-encodings' 'xorg-fonts-misc' 'xorg-fonts-type1' 'xorg-fonts-cyrillic'
		'alacritty' 'thunar' 'geany'
		'rofi' 'dunst'
		'mpd' 'mpc'
		'maim' 'xclip' 'viewnior'
		'ksuperkey' 
		'betterlockscreen'
		'xfce4-power-manager' 
		'xsettingsd'
		'sxhkd'
		'hsetroot'
		'wmname'
		'pulsemixer' 'light' 'xcolor'
)
conflicts=()
provides=("${pkgname}")
options=(!strip !emptydirs)
install="${pkgname}.install"

prepare() {
	cp -af ../files/. ${srcdir}
}

package() {
	local _config=${pkgdir}/etc/skel/.evilwm
	mkdir -p "$_config"

	# Copy cwm config files
	cp -r ${srcdir}/alacritty 		"$_config"
	cp -r ${srcdir}/scripts 		"$_config"
	cp -r ${srcdir}/theme 			"$_config"

	chmod +x "$_config"/scripts/*
	chmod +x "$_config"/theme/polybar.sh
	chmod +x "$_config"/theme/polybar/launch.sh
	chmod +x "$_config"/theme/polybar/scripts/bluetooth.sh

	install -Dm 644 dunstrc   				"$_config"/dunstrc
	install -Dm 644 picom.conf   			"$_config"/picom.conf
	install -Dm 644 picom-ibhagwan.conf   	"$_config"/picom-ibhagwan.conf
	install -Dm 644 picom-jonaburg.conf   	"$_config"/picom-jonaburg.conf
	install -Dm 644 picom-original.conf   	"$_config"/picom-original.conf
	install -Dm 644 sxhkdrc   			    "$_config"/sxhkdrc
	install -Dm 644 xsettingsd   			"$_config"/xsettingsd

	install -Dm 644 .evilwmrc   			     ${pkgdir}/etc/skel/.evilwmrc

	install -Dm 755 run-evilwm   			     ${pkgdir}/usr/local/bin/run-evilwm
	install -Dm 644 archcraft-hook-evilwm.hook   ${pkgdir}/usr/share/libalpm/hooks/archcraft-hook-evilwm.hook
}
