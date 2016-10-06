Gnome HUD Menu
===========
Provides a text based keyboard navigatable HUD menu for certain GTK apps which runs menubar commands through dmenu.

![Inkscape](/Genesis/Profiles/Loren/Workspace/gnome-hud-menu/example-inkscape.png  "Inkscape Gnome HUD Menu example")

Works With
====
* GIMP
* Inkscape
* HexChat
* Snes9x

Doesn't Work With
====
* Firefox
* Nautilus
* Chrome
* Krita

Dependencies
============
* python-dbus
* dmenu
* ?


Installation
====

Step 1
Install to the Optional directory


	cd /opt

Step 2
Clone Gnome HUD Menu

	sudo git clone https://github.com/ElectricPrism/gnome-hud-menu.git

Step 3
Execute this to append to your ~/.profile

	cat <<EOT >> ~/.profile
	
	if [ -n "$GTK_MODULES" ]
	then
	  GTK_MODULES="$GTK_MODULES:unity-gtk-module"
	else
	  GTK_MODULES="unity-gtk-module"
	fi
	
	if [ -z "$UBUNTU_MENUPROXY" ]
	then
	  UBUNTU_MENUPROXY=1
	fi
	
	EOT




gnome-appmenu-service.py
=====================
Incomplete implementation of the com.canonical.AppMenu.Registrar DBus service.
Applications exporting their menu through dbusmenu need this service to run.

gnome-hud-menu.py
==============
Try to get the menu of the currently focused X11 window, list possible actions and ask the used which one to run.

gnome-wm config [ IGNORE ]
============
	exec /opt/gnome-hud-menu/gnome-appmenu-service.py
	
	bindsym $mod+x exec /opt/gnome-hud-menu/gnome-hud-menu.py



Gnome Control Center
====

Create a binding in [Gnome Control Center ] -> [ Keyboard ] -> [ Add ]

###Title
	Gnome HUD Menu

###Exec
	/opt/gnome-hud-menu/gnome-hud-menu.py

###Shortcut
	Super + X