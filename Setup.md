Steps to install an i3/arch dual boot with Windows on Thinkpad P1 Gen 2.

We follow [Arch Linux Install (UEFI) and Dual Boot with Windows 10 | A Step by Step Guide | 2020 Tutorial](https://www.youtube.com/watch?v=C3D_qzw94v8) for the most part and specify some key differences.

1. Set `Secure Boot` to `Disabled` in the BIOS in the Security settings. It is required to boot from arch USB drive.

1. Enter the boot menu by pressing F12 at startup then select the USB drive.

1. Network setup for installation

If `ping google.com` fails with "Name or service not known", we have a `dhcpc` problem: start the daemon:

```systemctl start dhcphcd.service```

1. 
