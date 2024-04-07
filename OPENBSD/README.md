OpenBSD
=======

💾 Install
----------

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

```sh
ungoogled-chromium \  #
clamav \  #
curl \  #
ezquake \  #
firefox-esr \  #
gimp \  #
git \
gtk+2 \
gtk2mm \
inkscape \
jdk \
jupyter-notebook \
kbreakout \
kajongg \
kcachegrind \
leafpad \
lxappearance \
lxqt \
lxqt-extras \
lxqt-panel \
lxqt-powermanagement \
lxqt-sudo \
lxqt-themes \
lxrandr \
lxterminal \
mplayer \
mtools \
mtpaint \
mupen64plus \
mypaint \
nano \
nasm \
node \
openbox \  #
pcmanfm \
pcmanfm-qt \
pcre++ \
pcre2 \
php \  #
python \
python-idle \
pylint3 \
ruby \
sdl2 \
seamonkey \
thunderbird \  #
tor \  #
tor-browser \  #
weechat \
wkhtmltopdf \
xcursor-themes \
```


💻 X Window System
------------------

    # rcctl enable xenodm
    # rcctl start xenodm


    xrandr --output default --mode 1600x900
    . $HOME/.profile
    startlxqt

* https://www.openbsd.org/faq/faq11.html
* https://www.x.org/archive/X11R7.5/doc/platforms/OpenBSD.html


Java / JDK
----------

/etc/man.conf <-- /usr/local/jdk-1.8.0/man


📨 Submit Device Info
---------------------

1. _Using both GENERIC.MP & GENERIC kernels:_

       # dmesg; sysctl hw.sensors >/root/my-stuff.txt

3. _Email to: <dmesg@openbsd.org>_
