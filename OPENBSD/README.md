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

    $ su
    # cd /etc
    # cp examples/doas.conf .
    # exit

    $ mail
    $ man afterboot
    $ man intro
    $ man packages
    $ man config

    # syspatch
    # vi /etc/ssh/sshd_config
      `PermitRootLogin no`
    
    $ date
    # ln -fs /usr/share/zoneinfo/US/Pacific /etc/localtime

    $ man ps
    $ man netstat
    $ man fstat

    # adduser
    # vi /etc/group
      `wheel:*:0:root,veganaiZe`

    $ man audio
    $ man video
    # vi /etc/sysctl.conf
      ```
      kern.audio.record=1
      kern.video.record=1
      ```

    $ man apmd
    $ man fbtab
    $ man crontab
    # crontab -l

    # pkg_add -u [pkgname(s)]  # Update specific package(s) or all
    $ pkg_info -Q unzip
    $ pkglocate mutool  # Find files in packages

    # pkg_add -v chromium firefox pkglocatedb
    # pkg_delete <pkg(s)>
    # pkg_delete -a

    $ man rc.d
    $ man rc
    # rcctl 

    /etc/rc.conf
    /etc/rc.conf.local
    /etc/rc.conf.d/


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

    xrandr --output default --mode <1600x900 | 1368x768>
    . $HOME/.profile
    startlxqt

-> DesktopSettings
  -> LXQt Settings
    -> Keyboard and Mouse
      -> Cursor
        -> whiteglass
        -> Size: 32

* https://www.openbsd.org/faq/faq11.html
* https://www.x.org/archive/X11R7.5/doc/platforms/OpenBSD.html


☕ Java / JDK
-------------

```
# nano /etc/man.conf
    `manpath /usr/local/jdk-1.8.0/man`
```


📨 Submit Device Info
---------------------

1. _Using both GENERIC.MP & GENERIC kernels:_

       # dmesg; sysctl hw.sensors >/root/my-stuff.txt

3. _Email to: <dmesg@openbsd.org>_
