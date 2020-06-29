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



## Fully functional i3 setup: wifi, GPU

1. Tools everybody needs

```
sudo pacman -S git fakeroot make gcc automake autoconf
```

Finally, install [yay](https://www.tecmint.com/install-yay-aur-helper-in-arch-linux-and-manjaro/) as your AUR package manager. Note that you get `go` as a dependency ;)

1. Install X, i3 and LightDM:

We will use LightDM as our display manager with `slick-greeter` and `i3-gaps` as our window manager.

```
sudo pacman -S xorg-server xorg-xinit i3-gaps i3status lightdm rxvt-unicode
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

and set scale and fonts if you have a high resolution screen:

```
~/.Xresources
Xft.dpi: 300
URxvt.font: xvt:Source Code Pro:size=14
```

To get the list of fonts, `fc-list` will return all the fonts accessible on your system.

## Beautify i3
