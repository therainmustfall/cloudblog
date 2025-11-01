+++
date = '2025-11-01T11:46:05+08:00'
draft = false
title = 'Create a Windows Bootable USB on Ubuntu'
+++


Using normal copy-paste method to write Windows ISO to a USB device on Ubuntu to boot on a windows machine is sometimes not applicable, as often on the installation start it will tell you it can't detect any compatible devices or something. WoeUSB is one of the sollutions that can solve the above problem.

## Install WoeUSB on Ubuntu:

```bash
# add repository
sudo add-apt-repository ppa:tomtomtom/woeusb
# maby need a sudo apt update to refresh package source

# install WoeUSB
sudo apt install woeusb woeusb-frontend-wxgtk
```

## Write ISO mirror to USB device

After the installation now you can search 'WoeUSB' in the applications and run it. First it will show you a big message box that makes you panic but actually telling you don't panic. After your confirmation, you will meet its user interface. Finally,you umount the USB device in the Gparted application before burning the ISO into it.


## references:

[linux-terminal](https://cn.linux-terminal.com/?p=6530)
