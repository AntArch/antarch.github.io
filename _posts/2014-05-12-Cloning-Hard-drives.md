---
Date: 2014-05-12 11:00
Title: Cloning hard drives in Linux
Category: IT, Linux, Clone, Disaster recovery
Tags: IT, Linux, Clone, Disaster recovery
layout: post
---

# Metadata

This document is formatted using MarkDown

This work was done by Anthony Beck, [OrcID: 0000-0002-2991-811X](http://orcid.org/0000-0002-2991-811X).

A request from Adrian Porter

# Cloning Hard-Drives

At our stand-up today Mark Farrington raised a point about disaster recovery for people working remotely - this pertained to both data and systems. I chipped in that I use a linux live USB and clone the full system drive to an external and can then use that to recreate the drive if it all goes pear shaped. Adrian Porter asked for an overview.

My approach uses the command line (terminal) and a programme called gparted. You also need a Live USB. I would recommend [linux mint](http://www.linuxmint.com/) cinnamon or mate editions. If you're in windows there are numerous guides to downloading and installing these ISOs onto USB sticks. You'll need a 2gb+ USB stick.

Once you've created your bootable USB stick then insert it into your laptop and reboot. It should detect the drive and boot into it. If not you'll either need to go into bios or change your boot order to tell the machine to boot from that device (again Google is your friend).

Once you're in linux mint do the following:

* Read the archwiki on [disk cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
	* this is for the Arch linux system. Basically it's the best linux advice on the web. 
* *MAKE SURE YOU READ** the archwiki on [disk cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
* Open Gparted (*sudo gparted*)
* Get the name of your source drive
	* Look at your source size
* Get the name of your target drive
	* Ensure your target size is the same (or larger) than your source
* in a terminal type *sudo  dd if=*source drive (/dev/sda) *of=*target drive (/dev/sdb) *bs=4096 conv=notrunc,noerror,sync*
* Press return
* Wait, *patiently* until you see a new command prompt

That's it. 

To clone back after a disaster your source becomes your target and vice versa (don't worry about file size differences).

For info it took about 1 our to clone 240gb

[Here is a video explaining this](https://dl.dropboxusercontent.com/u/393477/Temp/Hard_drive_cloning.mkv)


