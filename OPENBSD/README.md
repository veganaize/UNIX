OpenBSD
=======

💾 Install
----------

(I)nstall
  - (us) keyboard layout

(C)ustom
  - (p)rint partitions
  - (a)dd partition


🔨 Post-install
---------------

    $ su
    # cd /etc
    # cp examples/doas.conf .
    # exit

    $ mail
    $ man afterboot
    $ man intro
    $ man packages

    # syspatch

    # pkg_add -u
    $ pkg_info -Q unzip
    $ pkglocate mutool

    # pkg_add -v chromium firefox pkglocatedb
    # pkg_delete <pkg(s)>
    # pkg_delete -a


/etc/rc.conf
/etc/rc.conf.local
/etc/rc.conf.d/


📦 Packages
-----------

https://mirrors.mit.edu/pub/OpenBSD/7.4/packages-stable/amd64/
https://mirrors.mit.edu/pub/OpenBSD/7.4/packages/amd64/

chromium*
clamav*
curl*
ezquake*
firefox-esr*
gimp*
git
gtk+2
gtk2mm
inkscape
jdk
jupyter-notebook
kbreakout
kajongg
kcachegrind
leafpad
lxappearance
lxqt
lxqt-extras
lxqt-panel
lxqt-powermanagement
lxqt-sudo
lxqt-themes
lxrandr
lxterminal
mplayer
mtools
mtpaint
mupen64plus
mypaint
nano
nasm
node
openbox*
pcmanfm
pcmanfm-qt
pcre++
pcre2
php*
python
python-idle
pylint3
ruby
sdl2
seamonkey
thunderbird*
tor*
tor-browser*
weechat
wkhtmltopdf
xcursor-themes


💻 X Window System
------------------

    # rcctl enable xenodm
    # rcctl start xenodm


    xrandr --output default --mode 1600x900
    . $HOME/.profile
    startlxqt

https://www.openbsd.org/faq/faq11.html
https://www.x.org/archive/X11R7.5/doc/platforms/OpenBSD.html


📨 Submit Device Info
---------------------

1. _Using both GENERIC.MP & GENERIC kernels:_

       # dmesg; sysctl hw.sensors >/root/my-stuff.txt

3. _Email to: <dmesg@openbsd.org>_
