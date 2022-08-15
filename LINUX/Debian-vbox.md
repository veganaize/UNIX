Install Debian GNU/Linux
========================

* [Installation Guide](https://www.debian.org/releases/bullseye/installmanual)

* Download & mount [Debian 11 netinst ISO](https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-11.4.0-amd64-netinst.iso):
    - in VirtualBox Manager -> Right-click `Debian 11` -> `Settings...`
        - `Storage` -> `Controller: ...` -> :cd: : Empty -> Optical Drive: `Choose a disk file...` -> debian-11.4.0-amd64-netinst.iso

* `LXDE` (only) --> 1126 packages --> ~5 gigs to unpack & install

* Switch Virtual Terminals:
    - Installation details (console): `CTRL`+`ALT`+`F4`
    - Restore GUI view: `ALT`+`F5`

* _Login as normal (non-root) user!_


Desktop Settings
================

Desktop Resolution
------------------
1. Resize display: Desktop Taskbar Menu -> `Preferences` -> `Monitor Settings` -> 1280x768 -> `Apply` & `Save`
2. VirtualBox Menu Bar -> `View` -> `Adjust Window Size` ((right)`CTRL`+`A`)


Arrangement & Colors
--------------------
* Taskbar Position:
    - Right-click Desktop Task Bar -> `Panel Settings` -> Position Edge: Top
* Look & Feel:
    - Desktop Taskbar Menu -> `Preferences` -> `Customize Look and Feel` -> Adwaita-dark -> `Apply`


Screensaver
-----------
* Desktop Taskbar Menu -> `Preferences` -> `Screensaver` -> Mode: `Disable Screen Saver`


File Manager
------------
* Desktop Taskbar Menu -> `System Tools` -> `File Manager PCManFM`
    - PCManFM Menu Bar -> `Edit` -> `Preferences`
        - Uncheck: Move deleted files to "trash can" ...


LXTerminal
----------
* Create Desktop Shorcut:
    - Desktop Taskbar Menu -> `System Tools` -> Right-click `LXTerminal` -> Add to desktop
* Customize LXTerminal:
    - LXTerminal Menu Bar -> `Edit` -> `Preferences`
        - Terminal Font: `Monospace` `Bold` `18`
        - Palette: `Tango` or `Solarized Dark`
        - `Display` -> Scrollback lines: 10000


Console Stuff
=============

* Add user to sudo:
```bash
$ su -c "/sbin/usermod -aG sudo username"
```
Desktop Taskbar Menu -> `Logout` -> `Logout`
(then log back in...)


* 3.4 gigs used after install:
```bash
$ df -h /dev/sda1
```


* List Installed Packages:
[dpkg-query](https://manpages.debian.org/bullseye/dpkg/dpkg-query.1.en.html)
```bash
$ dpkg-query -l >installed-packages.txt
```
PCManFM -> Right-click "installed-packages.txt" -> `Open With...`
    - Check: Set selected application as default action ...
    - `Accessories` -> `Mousepad` -> `OK`


* Expand Repositories:
```bash
$ sudo nano -w /etc/apt/sources.list
```
Append ` contrib non-free` to all entries
`CTRL+X`, `Y`, `ENTER`


* Update system:
```bash
$ sudo apt-get update
$ sudo apt-get upgrade --show-upgraded
```


* Install some packages:
```bash
$ sudo apt-get install build-essential dkms linux-headers-$(uname -r) idle3 python3-pip chromium gimp inkscape keepassxc
$ sudo apt-get clean
```
(+~713 MB after installation -- 4.1 GB total for system)


* Install VirtualBox Guest Additions:
VirtualBox Menu Bar -> `Devices` -> `Insert Guest Additions CD Image...`
```bash
$ mount /media/cdrom
$ cd /media/cdrom
$ sudo bash ./VBoxLinuxAdditions.run

$ /sbin/rcvboxadd quicksetup all #For all installed kernels
$ /sbin/rcvboxadd setup
$ less /var/log/vboxadd-setup.log
```
Desktop Taskbar Menu -> `Logout` -> `Reboot`


Synaptic Package Manager
========================
* Taskbar Menu -> `Preferences` -> `Synaptic Package Manager`
    - Menu Bar -> `Settings` -> `Preferences`
        - Uncheck: Consider recommended packages as dependencies
        - Check: Apply changes in a terminal window
        - `Files` -> Check: Delete downloaded packages after installation
    - Click `Reload` in toolbar
    - Click `Search` in toolbar -> type `nodejs` -> Look in: `Name` (only) -> `Search`
        - Right-click `nodejs` -> `Mark for installation` -> `Mark`


Configure Python / IDLE
=======================

* IDLE Menu Bar -> `Options` -> `Configure IDLE`
    - Font Size: 18 Bold
    - Highlights -> Highlighting Theme: IDLE Dark

* Install / upgrade 3rd-party libraries:
```bash
$ pip3 install --upgrade pygame
$ pip3 cache purge
```
