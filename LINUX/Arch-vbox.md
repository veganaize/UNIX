[ArchLinux Install Guide](https://wiki.archlinux.org/title/Installation_guide)
========================================

* [Download Image](https://geo.mirror.pkgbuild.com/iso/latest/archlinux-x86_64.iso)

```bash
ping -c 3 example.com
```

```
fdisk /dev/sda
```
1.  `m`enu
2.  `o` - create a new empty DOS partition table
3.  `n` - add a new partition
4.  `p`rimary
5.  `ENTER`
6.  `ENTER`
7.  `ENTER`
8.  `y`es remove signature, if asked
9.  `t`ype -> `linux`
10. `a` - toggle bootable flag
11. `w`rite table to disk and exit
```
reboot
```

```
mkfs.ext2 -q /dev/sda1
```

```
mount /dev/sda1 /mnt  ## Every time ##
```

* [Live System Package List](https://geo.mirror.pkgbuild.com/iso/latest/arch/pkglist.x86_64.txt)

```
pacstrap /mnt base linux-zen nano man-db man-pages texinfo
```

```
genfstab -U /mnt >> /mnt/etc/fstab
```

```
arch-chroot /mnt  ## Every time ##
```

```
ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
```

```
nano -w /etc/locale.gen
```
1. Uncomment `en_US.UTF-8 UTF-8`
2. `CTRL+X` -> `Y` -> `ENTER`

```
locale-gen
nano -w /etc/locale.conf
```
1. `LANG=en_US.UTF-8`
2. `CTRL+X` -> `Y` -> `ENTER`

```
passwd
```
1. Enter a pin number or something

```bash
pacman -S grub
grub-install --target=i386-pc /dev/sda

nano -w /etc/default/grub
```
1. `GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet mitigations=off"`

```bash
grub-mkconfig -o /boot/grub/grub.cfg

exit
reboot
```
1. VirtualBox Menu Bar --> `Devices` -> `Optical Drives` -> `Remove disc from virtual drive`
2. `Force Unmount` (if necessary)
3. VirtualBox Menu Bar --> `Machine` -> `Reset` (or `HOST+R`)


[General Recommendations](https://wiki.archlinux.org/title/General_recommendations)
========================================

Network
----------------------------------------

`networkctl list`
`nano -w /etc/systemd/network/20-wired.network`
```
[Match]
Name=enp0s3

[Network]
DHCP=yes
```

`systemctl enable systemd-networkd.service`
`systemctl start  systemd-networkd.service`
`systemctl enable systemd-resolved.service`
`systemctl start  systemd-resolved.service`


Pacman
----------------------------------------

_Update:_
`pacman -Syyu`

_Search:_
`pacman -Ss string1 string2 ...`

_Info:_
`pacman -Si <package>`

_Install:_
`pacman -S <package(s)>`

_Clean:_
`pacman -Scc`

_Remove:_
`pacman -Rs <package>`


```
pacman -S reflector \
          base-devel \
          colorgcc \
          python \
          python-pip \
          gpm \
```


Users
----------------------------------------

`useradd -m -G ftp,games,http,sys,uucp,wheel <username>`
`passwd <username>`

`EDITOR=nano visudo`
    --> `%wheel ALL=(ALL:ALL) NOPASSWD: ALL`


Color Console
----------------------------------------
`nano -w ~/.bashrc`
```
alias diff='diff --color=auto'
alias grep='grep --color=auto'
alias ip='ip -color=auto'
alias ls='ls --color=auto'

export LESS='-R --use-color -Dd+r$Du+b'
```

`nano -w /etc/pacman.conf`
    --> Uncomment the Color line


X11
========================================

```
pacman -S lxde \
          xorg \
          xorg-xinit \
          xf86-video-vesa \
          xf86-video-fbdev \
          leafpad \
          chromium \
          tk \
          ttf-dejavu \
          ttf-droid \
```

`Xorg :0 -configure`
`mv /root/xorg.conf.new /etc/X11/xorg.conf`
`nano -w /etc/X11/xorg.conf`
```
Section "Monitor"
    Option "PreferredMode" "1920x1080"

Section "Screen"
    DefaultDepth 24

    SubSection "Display"
        Modes "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
```

`nano -w ~/.xinitrc`
```
exec startlxde
```


[VirtualBox Guest Additions](https://wiki.archlinux.org/title/VirtualBox/Install_Arch_Linux_as_a_guest)
========================================

VBox Menubar -> `Devices` -> `Insert Guest Additions CD image...`
```
$ sudo pacman -S linux-zen-headers
$ sudo mount /dev/cdrom /mnt
$ sudo bash /mnt/VBoxLinuxAdditions.run
```
Desktop Taskbar Menu -> `Logout` -> `Reboot`


3D Acceleration
========================================
* Right-click virtual machine -> `Settings` -> `Display`
    - Video Memory: `128 MB`
    - `Check`: Enable 3D Acceleration
```
sudo pacman -S mesa-utils xf86-video-vmware
```
_Restart X..._
```
glxinfo |grep OpenGL
glxgears
```


[ArchWiki](https://wiki.archlinux.org/)
