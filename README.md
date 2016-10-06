gnome-hud-menu
===========

Provides a way to run menubar commands through dmenu.

Dependencies
============
* python-dbus
* dmenu
* ?

gnome-appmenu-service.py
=====================
Incomplete implementation of the com.canonical.AppMenu.Registrar DBus service.
Applications exporting their menu through dbusmenu need this service to run.

gnome-hud-menu.py
==============
Try to get the menu of the currently focused X11 window, list possible actions and ask the used which one to run.

Add to

~/.profile

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



gnome-wm config
============
    exec ~/.gnome/gnome-appmenu-service.py
    bindsym $mod+x exec ~/.gnome/gnome-hud-menu.py
    
Note
====
Firefox does not seem to export its menus properly through dbusmenu (with the ubuntu patch and ui.use_unity_bar enabled) ...



Create a binding in Gnome Control Center -> Keyboard
Title: Gnome HUD Menu
Exec: /opt/gnome-hud-menu/gnome-hud-menu.py
Shortcut: Super + X



cd /opt

git clone https://.git

# mkdir /opt/gnome-hud-menu