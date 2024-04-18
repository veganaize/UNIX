OpenBSD
=======

💾 Install
----------

_VirtualBox: Machine -> Settings -> System -> Pointing Device: USB Tablet_

```
[I]nstall
  - [us] keyboard layout

[C]ustom
  - [h]elp
  - [p]rint partitions
  - [z] delete all partitions
  - [a]dd partition
    - partition to add: [a]
    - offset: [64]
    - size: [########]
    - FS type: [4.2BSD]
    - mount point: /
  - [w]rite label to disk
  - [q]uit, saving changes

Location of sets: http
  - HTTP server: mirrors.mit.edu
```


🔨 Post-install
---------------

<pre>
$ <a href="https://man.openbsd.org/su">su</a>
# <a href="https://man.openbsd.org/sh#cd">cd</a> /etc
# <a href="https://man.openbsd.org/cp">cp</a> examples/doas.conf .
# <a href="https://man.openbsd.org/sh.1#exit">exit</a>

$ man <a href="https://man.openbsd.org/mail">mail</a>
$ man <a href="https://man.openbsd.org/afterboot">afterboot</a>
$ man <a href="https://man.openbsd.org/intro">intro</a>
$ man <a href="https://man.openbsd.org/packages">packages</a>
$ man <a href="https://man.openbsd.org/config">config</a>

# <a href="https://man.openbsd.org/syspatch">syspatch</a>
# <a href="https://man.openbsd.org/vi">vi</a> /etc/ssh/sshd_config
  `PermitRootLogin no`

$ <a href="https://man.openbsd.org/date">date</a>
# <a href="https://man.openbsd.org/ln">ln</a> -fs /usr/share/zoneinfo/US/Pacific /etc/localtime

$ man <a href="https://man.openbsd.org/ps">ps</a>
$ man <a href="https://man.openbsd.org/netstat">netstat</a>
$ man <a href="https://man.openbsd.org/fstat">fstat</a>

# <a href="https://man.openbsd.org/adduser">adduser</a>
# vi /etc/group
  `wheel:*:0:root,veganaiZe`

$ man <a href="https://man.openbsd.org/audio">audio</a>
$ man <a href="https://man.openbsd.org/video">video</a>
# vi /etc/sysctl.conf
  ```
  kern.audio.record=1
  kern.video.record=1
  ```

$ man <a href="https://man.openbsd.org/apmd">apmd</a>
$ man <a href="https://man.openbsd.org/fbtab">fbtab</a>
$ man <a href="https://man.openbsd.org/crontab">crontab</a>
# crontab -l

# <a href="https://man.openbsd.org/pkg_add">pkg_add</a> -u [pkgname(s)]  # Update specific package(s) or all
$ <a href="https://man.openbsd.org/pkg_info">pkg_info</a> -Q unzip
$ <a href="https://man.openbsd.org/pkglocate">pkglocate</a> mutool  # Find files in packages

# pkg_add -v chromium firefox pkglocatedb
# <a href="https://man.openbsd.org/pkg_delete">pkg_delete</a> <pkg(s)>
# pkg_delete -a

$ man <a href="https://man.openbsd.org/rc.d">rc.d</a>
$ man <a href="https://man.openbsd.org/rc">rc</a>
# <a href="https://man.openbsd.org/rcctl">rcctl</a> 

/etc/<a href="https://man.openbsd.org/rc.conf">rc.conf</a>
/etc/<a href="https://man.openbsd.org/rc.conf.local">rc.conf.local</a>
/etc/rc.conf.d/
</pre>


📦 Packages
-----------

* https://mirrors.mit.edu/pub/OpenBSD/7.5/packages-stable/amd64/
* https://mirrors.mit.edu/pub/OpenBSD/7.5/packages/amd64/

<pre>
Editors
-------

elvis \
ffmpeg \
<a href="https://www.geany.org/">geany</a> \
gedit \
<a href="https://www.gimp.org/">gimp</a> \  #
<a href="https://inkscape.org/">inkscape</a> \
<a href="https://kate-editor.org/">kate</a> \
<a href="https://kdenlive.org/en/">kdenlive</a> \
kdevelop \
<a href="http://tarot.freeshell.org/leafpad/">leafpad</a> \
mtpaint \
mypaint \
nano \
<a href="https://en.wikipedia.org/wiki/NEdit">nedit</a> \
netbeans \
<a href="https://en.wikipedia.org/wiki/IDLE">python-idle</a> \
synfig \
synfigstudio \
vim \
wkhtmltopdf \


Games
-----

ezquake \  #
gtypist \
kajongg \
kalgebra \
kbreakout \
kguitar \
klogic \
ktouch \
minecraft \
<a href="https://mupen64plus.org/">mupen64plus</a> \
nyancat \
vega-strike \


Internet
--------

curl \  #
firefox-esr \  #
nmap \
nmap-zenmap \
seamonkey \
thunderbird \  #
tor \  #
tor-browser \  #
ungoogled-chromium \  #
wget \
<a href="https://weechat.org/about/">weechat</a> \


Programming
-----------

<a href="https://liballeg.org/">allegro</a> \
apache-ant \
apktool \
clojure \
gcc \
g++ \
git \
gmake \
<a href="https://developer-old.gnome.org/gtk2/2.24/">gtk+2</a> \
gtk2mm \
<a href="https://en.wikipedia.org/wiki/OpenJDK">jdk</a> \
<a href="https://jlint.sourceforge.net/">jlint</a> \
jupyter-notebook \
kcachegrind \
lwjgl \
maven \
mlt \
nasm \
node \
<a href="http://robhagemans.github.io/pcbasic/">pcbasic</a> \
pcre++ \
pcre2 \
php \  #
postgresql-* \
python \
pylint3 \
ruby \
scala \
sdl2 \
sfml \


Util
----

anki \
bible-kjv \
<a href="https://www.clamav.net/">clamav</a> \  #
<a href="https://i3wm.org/">i3</a> \
lxappearance \
<a href="https://lxqt-project.org/">lxqt</a> \
lxqt-extras \
lxqt-panel \
lxqt-powermanagement \
lxqt-sudo \
lxqt-themes \
lxrandr \
lxterminal \
mc \
mplayer \
mpv \
mtools \
openbox \  #
os-test \
<a href="https://github.com/lxde/pcmanfm">pcmanfm</a> \
<a href="https://github.com/lxqt/pcmanfm-qt">pcmanfm-qt</a> \
smplayer \
smtube \
xcursor-themes \
<a href="https://zsh.sourceforge.io/">zsh</a> \
</pre>


💻 X Window System
------------------

    # rcctl enable xenodm
    # rcctl start xenodm

    $ nano -w ~/.xsession
        export LC_CTYPE="en_US.UTF-8"
        xrandr --output default --mode <1600x900 | 1366x768>
        . $HOME/.profile
        startlxqt

_Desktop Menu: DesktopSettings -> LXQt Settings -> Keyboard and Mouse -> Cursor -> whiteglass -> Size: 32_

* https://www.openbsd.org/faq/faq11.html
* https://www.x.org/archive/X11R7.5/doc/platforms/OpenBSD.html


☕ Java / JDK
-------------

```
# nano -w /etc/man.conf
    `manpath /usr/local/jdk-1.8.0/man`
```


📨 Submit Device Info
---------------------

1. _Using both GENERIC.MP & GENERIC kernels:_

       # dmesg; sysctl hw.sensors >/root/my-stuff.txt

3. _Email to: <dmesg@openbsd.org>_
