+++
date = '2025-11-01T11:58:08+08:00'
draft = false
title = 'Installing a Virtual Machine on Ubuntu 24.04'
+++

## Check virtualization support

```bash
LC_ALL=C.UTF-8 lscpu | grep Virtualization
```

## Load KVM (Kernel-based Virtual Machine)

```bash
lsmod | grep kvm   # check if KVM is loaded
```
   If not loaded, type:
   ```bash
   sudo modprobe -a kvm kvm_intel
   # or
   sudo modprobe -a kvm kvm_amd # for AMD processor
   ```

## Intall QEMU ( command line and graphical tool, e.g., Virtual Machine Manager )

```bash
sudo apt install qemu-system
```

## Install QEMU/KVM virtual machines: Virtual Machine Manager

```bash
sudo apt install virt-manager
```

add user to libvirt group and start the sevice:

```bash
sudo gpasswd --add $USER libvirt
sudo systemctl start libvirtd
```

## virtual graphical interface installation and configuring user ownership

editing the libvirtd config (to uncomment unix_sock_group and unix_sock_rw_perms):

```bash
sudo nano /etc/libvirt/libvirtd.conf
```

editing qemu config (to set "user = " and "group = " to current user), then restart service:

```bash
sudo nano /etc/libvirt/qemu.conf
# after editing and saving
sudo systemctl restart libvirtd.service
```

Finally installed virtual machine on ubuntu 24.04 after trying VMware WorkStation and Virtualbox.The above approach is from [ubuntuhandbook](https://ubuntuhandbook.org/index.php/2024/12/kvm-qemu-virtual-machines-ubuntu/#:~:text=This%20is%20a%20step%20by%20step%20guide%20shows,virtual%20machines%20using%20qemu%2Fkvm%20solution%20in%20Ubuntu%2024.04.). I just installed a Windows system and I haven't tried more such as sharing folders. More configuration and illustration is on the link page.

## More references:

1. [archlinux](https://wiki.archlinux.org/title/Virt-manager)
2. [sspai](https://sspai.com/post/80638)
3. [virt-manager](https://virt-manager.org/)

