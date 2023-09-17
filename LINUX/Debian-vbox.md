Install Debian GNU/Linux in VirtualBox
======================================

1. Download & install [VirtualBox](https://www.virtualbox.org/)

[_Debian's Installation Guide_](https://www.debian.org/releases/bullseye/installmanual)

2. Download & mount [Debian netinst ISO](https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/)
    - VirtualBox Manager Menu Bar -> `Machine` -> `New`
        - Name: `Debian`
        - Memory size: `2048 MB`
        - `Check`: Create a virtual hard disk now -> `Create` -> `16 GB` -> `VDI` -> `Check`: Dynamically allocated -> `Create`
    - VirtualBox Manager -> right-click `Debian 11` -> `Settings`
        - `Storage` -> Controller: -> 💿 Empty -> Optical Drive 💿 `Choose a disk file...` -> debian-*-netinst.iso -> `OK`

3. VirtualBox Manager -> double-click `Debian`

4. `LXDE` (only) --> 1126 packages --> ~5 gigs to unpack & install

5. Switch Virtual Terminals:
    - Installation details (console): `CTRL`+`ALT`+`F4`
    - Restore GUI view: `ALT`+`F5`

6. _Login as normal (non-root) user!_


Desktop Settings
================

Desktop Resolution
------------------
1. Desktop Taskbar Menu -> `Preferences` -> `Monitor Settings` -> `800x600` -> `Apply` & `Save`
2. VirtualBox Menu Bar -> `View` -> `Adjust Window Size`


Arrangement & Colors
--------------------
* Taskbar Position:
    - right-click Desktop Taskbar -> `Panel Settings` -> Position Edge: `Top`
* Look & Feel:
    - Desktop Taskbar Menu -> `Preferences` -> `Customize Look and Feel` -> `Adwaita-dark` -> `Apply`


Screensaver
-----------
* Desktop Taskbar Menu -> `Preferences` -> `Screensaver` -> Mode: `Disable Screen Saver`
```bash
su -c "nano -w /etc/xdg/lxsession/LXDE/autostart"

## Comment out... ##
#@xscreensaver -no-splash
```


File Manager
------------
* Desktop Taskbar Menu -> `System Tools` -> `File Manager PCManFM`
    - PCManFM Menu Bar -> `Edit` -> `Preferences`
        - `Uncheck`: Move deleted files to "trash can" ...


LXTerminal
----------
* Create Desktop Shorcut:
    - Desktop Taskbar Menu -> `System Tools` -> right-click `LXTerminal` -> `Add to desktop`
* Customize LXTerminal:
    - LXTerminal Menu Bar -> `Edit` -> `Preferences`
        - Terminal Font: `Monospace` `Bold` `18`
        - Palette: `Tango` or `Solarized Dark`
        - `Display` -> Scrollback lines: `10000`


Console Stuff
=============

Add user to sudo
----------------
```bash
su -c "/sbin/usermod -aG sudo username"
```
1. Desktop Taskbar Menu -> `Logout` -> `Logout`
2. _Then log back in..._


Space available / utilized
--------------------------
```bash
df -h /dev/sda1
```


List installed packages
-----------------------
```bash
dpkg-query -l > ~/installed-packages.txt
```
* PCManFM -> right-click "installed-packages.txt" -> `Open With...`
    - `Check`: Set selected application as default action ...
    - `Accessories` -> `Mousepad` -> `OK`


Expand repositories
-------------------
```bash
sudo nano -w /etc/apt/sources.list
```
1. Append ` contrib non-free` to all entries
2. `CTRL+X` -> `Y` -> `ENTER`


Update system
-------------
```bash
sudo apt-get update
sudo apt-get upgrade --show-upgraded
```


Install some packages
---------------------
```bash
sudo apt-get install chromium gimp inkscape keepassxc
sudo apt-get clean
```


Install VirtualBox Guest Additions
==================================

* VirtualBox Menu Bar -> `Devices` -> `Insert Guest Additions CD Image...`
```bash
sudo apt-get install build-essential dkms linux-headers-$(uname -r)
sudo apt-get clean

mount /media/cdrom
cd /media/cdrom
sudo bash ./VBoxLinuxAdditions.run

## Other Kernels & Troubleshooting ##
/sbin/rcvboxadd quicksetup all #For all installed kernels
/sbin/rcvboxadd setup
less /var/log/vboxadd-setup.log
```
* Desktop Taskbar Menu -> `Logout` -> `Reboot`


Synaptic Package Manager
========================

* Desktop Taskbar Menu -> `Preferences` -> `Synaptic Package Manager`
    - Synaptic Menu Bar -> `Settings` -> `Preferences`
        - `Uncheck`: Consider recommended packages as dependencies
        - `Check`: Apply changes in a terminal window
        - `Files` -> `Check`: Delete downloaded packages after installation
    - Click `Reload` in toolbar
    - Click `Search` in toolbar -> type `nodejs` -> Look in: `Name` (only) -> `Search`
        - right-click `nodejs` -> `Mark for installation` -> `Mark`
    - Click `Apply` in toolbar


Python + IDLE
=============

```bash
sudo apt-get install idle3 python3-pip
sudo apt-get clean
```
_To configure IDLE..._
* Desktop Taskbar Menu -> `Programming` -> `IDLE`
    - IDLE Menu Bar -> `Options` -> `Configure IDLE`
        - Font Size: `18` `Bold`
        - Highlights -> Highlighting Theme: `IDLE Dark`

_To install / upgrade 3rd-party libraries..._
```bash
pip3 install --upgrade pygame
pip3 cache purge
```


Completely Remove LibreOffice
=============================

```bash
sudo apt-get purge -s libreoffice*
sudo apt-get autoremove
sudo apt-get clean
```


3D Video Acceleration
=====================
* Desktop Taskbar Menu -> `Logout` -> `Shutdown`
* VirtualBox Manager -> right-click `Debian 11` -> `Settings...` -> `Display`
    - Video Memory: `128 MB`
    - Graphics Controller: `VMSVGA`
    - `Check`: Enable 3D Acceleration
* VirtualBox Manager -> double-click `Debian 11`
```bash
glxinfo | grep OpenGL
glxgears
```
