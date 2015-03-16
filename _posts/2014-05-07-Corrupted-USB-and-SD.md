Date: 2014-04-20 20:00
Title: Corrupted USB and SD card
Category: IT, USB, SD, corrupt
Tags: IT, USB, SD, corrupt

# Metadata

This document is formatted using MarkDown

This work was done by Anthony Beck, [OrcID: 0000-0002-2991-811X](http://orcid.org/0000-0002-2991-811X).

# Data analysis

I've been doing a lot of ISO writing to USB and SD drives recently - #dontAsk. I've been getting a rather worrying number of these:

> Invalid partition table - recursive partition on /dev/****

To fix this go into terminal and do the following:

> sudo dd if=/dev/zero of=/dev/AAAAAA bs=1M

where AAAAAA refers to your drive (normally sdb or sdc).

This takes quite a long time to process. Once complete re-configure your drive in Gparted.

