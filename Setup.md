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

## Fully functional i3 Setup

## Beautify i3
