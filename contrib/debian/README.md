
Debian
====================
This directory contains files used to package addmored/addmore-qt
for Debian-based Linux systems. If you compile addmored/addmore-qt yourself, there are some useful files here.

## addmore: URI support ##


addmore-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install addmore-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your addmore-qt binary to `/usr/bin`
and the `../../share/pixmaps/addmore128.png` to `/usr/share/pixmaps`

addmore-qt.protocol (KDE)

