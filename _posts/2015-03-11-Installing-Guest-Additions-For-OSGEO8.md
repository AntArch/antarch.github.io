---
Date: 2015-03-11 10:47
Title: Installing Guest Additions for VirtualBox on OSGEO8
Category: virtual box, ubuntu, mint, OSGeo
Tags:  virtual box, ubuntu, mint, OSGeo
layout: post
---

# Installing Guest additions

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install virtualbox-guest-dkms
sudo apt-get install dkms
sudo apt-get install virtualbox-guest-x11
sudo apt-get install virtualbox-guest-utils
cd /media
ls
cd user/
ls
cd VBOXADDITIONS_4.3.10_93012/
sudo apt-get install gcc 
sudo apt-get install make
sudo ./VBoxLinuxAdditions.run 
sudo reboot now
```


# Accessing a shared drive

sudo adduser user vboxsf

(in general for each user do: sudo adduser <username> vboxsf)
