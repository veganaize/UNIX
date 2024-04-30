[ArchLinux Install Guide](https://wiki.archlinux.org/title/Installation_guide)
========================================

* [Download .ISO Install Image](https://geo.mirror.pkgbuild.com/iso/latest/archlinux-x86_64.iso)

```bash
ping -c 3 example.com
```

```bash
fdisk /dev/sda
```
1.  `m`enu
2.  `o` - create a new empty DOS partition table
3.  `n` - add a new partition
4.  `p`rimary
5.  `ENTER` default: 1
6.  `ENTER` default: 2048
7.  `ENTER` default
8.  `y`es remove signature _(only if asked)_
9.  `t`ype -> `linux`
10. `a` - toggle bootable flag
11. `w`rite table to disk and exit
```bash
reboot
```

```bash
mkfs.ext2 -q /dev/sda1
```

```bash
mount /dev/sda1 /mnt  ## Every time ##
```

[_Live System Package List_](https://geo.mirror.pkgbuild.com/iso/latest/arch/pkglist.x86_64.txt)

```bash
pacman --needed -Syy archlinux-keyring [parabola-keyring] [archlinux32-keyring]
```

```bash
nano -w /etc/pacman.d/mirrorlist
nano -w /etc/pacman.conf
    ParallelDownloads=5
```

```bash
pacstrap /mnt [parabola-]base linux[-libre]-lts nano man-db man-pages texinfo
```

```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

```bash
arch-chroot /mnt  ## Every time ##
```

```bash
ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
```

```bash
nano -w /etc/locale.gen
```
1. _Uncomment:_ `en_US.UTF-8 UTF-8`
2. `CTRL+X` -> `Y` -> `ENTER`

```bash
locale-gen
nano -w /etc/locale.conf
```
1. _Add:_ `LANG=en_US.UTF-8`
2. `CTRL+X` -> `Y` -> `ENTER`

```bash
mkinitcpio -p linux[-libre]-lts
```

```bash
passwd
```
_Then enter a pin number or something._

```bash
pacman -S grub
grub-install --target=i386-pc /dev/sda

nano -w /etc/default/grub
```
_Edit:_ `GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet mitigations=off"`

```bash
grub-mkconfig -o /boot/grub/grub.cfg

exit
reboot
```
1. VBox Menu Bar --> `Devices` -> `Optical Drives` -> `Remove disc from virtual drive`
2. `Force Unmount` _(as necessary)_
3. VBox Menu Bar --> `Machine` -> `Reset` (or `HOST+R`)


[General Recommendations](https://wiki.archlinux.org/title/General_recommendations)
========================================

Network
----------------------------------------

```bash
networkctl list
nano -w /etc/systemd/network/20-wired.network
```
_Add the following to the empty file..._
```
[Match]
Name=enp0s3

[Network]
DHCP=yes
```
`CTRL+X` -> `Y` -> `ENTER`

```bash
systemctl enable systemd-networkd.service
systemctl start  systemd-networkd.service
systemctl enable systemd-resolved.service
systemctl start  systemd-resolved.service
```

```bash
nano -w /etc/hosts
    127.0.0.1   localhost
    ::1	        localhost
    127.0.1.1   MY_HOSTNAME.localdomain myhostname
```


Pacman
----------------------------------------

Task                 | Command
:-------------------:|---------------------------------
___Update Keys___    | `pacman -S archlinux-keyring [parabola-keyring] [archlinux32-keyring]`
___Update___         | `pacman -Syyu`
___Search___         | `pacman -Ss string1 string2 ...`
___Info___           | `pacman -Si <package>`
___Install___        | `pacman -S <package(s)>`
___Clean___          | `pacman -Scc`
___Remove___         | `pacman -Rns <package>`
___Owned Files___    | `pacman -Ql <package>`
___Owning Package___ | `pacman -Qo <file>`
___Install (AUR)___  | `git clone https://aur.archlinux.org/somepackage.git`<br />`cd somepackage`<br />`makepkg -sirc`

---
```bash
pacman -S base-devel \
          python \
          python-pip \
          sudo \
```


[Users](https://wiki.archlinux.org/title/User:Gen2ly/Users_and_groups#Group_listings)
----------------------------------------

```bash
useradd -m -G audio,disk,ftp,games,http,lp,network,power,scanner,storage,sys,users,uucp,video,wheel <username>
passwd <username>

EDITOR=nano visudo
```
_Uncomment:_ `%wheel ALL=(ALL:ALL) NOPASSWD: ALL`


Color Console
----------------------------------------
```bash
nano -w ~/.bashrc
```
_Add these lines at the end of the file..._
```

alias diff='diff --color=auto'
alias grep='grep --color=auto'
alias ip='ip -color=auto'

export LESS='-R --use-color -Dd+r$Du+b'
```

```bash
nano -w /etc/pacman.conf
```
_Uncomment:_ `Color`


X11
========================================

```bash
pacman -S lxde \
          xorg \
          xorg-xinit \
          xf86-video-fbdev \
          xf86-video-vmware \
          leafpad \
          chromium \
          tk \
          ttf-dejavu \
          ttf-droid \
```

```bash
nano -w ~/.xinitrc
```
_Add the following line to the empty file..._
```
exec startlxde
```

_Extra stuff (skip to the next section)..._
```bash
Xorg :0 -configure
mv /root/xorg.conf.new /etc/X11/xorg.conf
nano -w /etc/X11/xorg.conf
```
```
Section "Monitor"
    Option "PreferredMode" "1920x1080"

Section "Screen"
    DefaultDepth 24

    SubSection "Display"
        Modes "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
```


[VirtualBox Guest Additions](https://wiki.archlinux.org/title/VirtualBox/Install_Arch_Linux_as_a_guest)
========================================

VBox Menubar -> `Devices` -> `Insert Guest Additions CD image...`
```bash
sudo pacman -S linux[-libre]-lts-headers gcc make
sudo mount /dev/cdrom /mnt
sudo bash /mnt/VBoxLinuxAdditions.run
```
Desktop Taskbar Menu -> `Logout` -> `Reboot`


3D Acceleration
========================================
* Right-click virtual machine -> `Settings` -> `Display`
    - Video Memory: `128 MB`
    - `Check`: Enable 3D Acceleration
```bash
sudo pacman -S mesa-utils xf86-video-vmware
```
_Restart X..._
```bash
glxinfo |grep OpenGL
glxgears
```


[_ArchWiki_](https://wiki.archlinux.org/)
