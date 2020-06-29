Steps to install an i3/arch dual boot with Windows on Thinkpad P1 Gen 2.

## Basic Arch Boot

We follow [Arch Linux Install (UEFI) and Dual Boot with Windows 10 | A Step by Step Guide | 2020 Tutorial](https://www.youtube.com/watch?v=C3D_qzw94v8) for the most part and specify some key differences.

1. Set `Secure Boot` to `Disabled` in the BIOS in the Security settings. It is required to boot from arch USB drive.

1. Enter the boot menu by pressing F12 at startup then select the USB drive.

1. Network setup for installation

If `ping google.com` fails with "Name or service not known", we may have a `dhcpc` problem. Start the daemon:

```systemctl start dhcpcd```

**Before rebooting**

1. Install `dhcpcd: 

```pacman -S dhcpcd```

and enable it:

```systemctl enable dhcpcd```

1. `sudo` and all...

```pacman -S sudo```

1. Make sure users from the `wheel` group can `sudo`:

```
EDITOR=vim visudo
```

and uncomment the lines that fit the behavior you want (with or without password).



## i3 & tools

### Build tools

```
sudo pacman -S git fakeroot make gcc automake autoconf
```

Finally, install [yay](https://www.tecmint.com/install-yay-aur-helper-in-arch-linux-and-manjaro/) as your AUR package manager.

### X, i3 and LightDM:

We will use LightDM as our display manager with `slick-greeter` and `i3-gaps` as our window manager.

```
sudo pacman -S xorg-server xorg-xinit i3-gaps i3status lightdm
yay install lightdm-slick-greeter
```

and set the greeter:

```
/etc/lightdm/lightdm.conf
[Seat:*]
...
greeter-session=lightdm-slick-greeter
...
```

And before rebooting:
```
sudo systemctl enable lightdm
```

For now, set scale and fonts if you have a high resolution screen -- otherwise, everything will look super tiny:

```
~/.Xresources
Xft.dpi: 300
```

When we setup multiple display, we will change the resolution of a lower resolution and drop the `dpi` configuration. Note that this is not really what we want to do but couldn't find a better way to far.

**Note** To get the list of fonts, `fc-list` will return all the fonts accessible on your system.

### NVidia and optimus-manager

TODO

### Sound

```
sudo pacman alsa-utils pulseaudio
```

### `URxvt`

### vim

See `.vimrc` for details.

### zsh

Install zsh and set to default.

Start `zsh` from i3:

```
bindsym $mod+Return exec urxvt -e /usr/bin/zsh
```

## Beautify i3
