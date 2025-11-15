---
title: Disk and Media Mounting, Greatest BASh Commands
description:
date: 2025-10-01
tags:
  - linux
layout: layouts/post.njk
---

## Recognizing a mounted USB for my MP3 Player:
```
  610  lsblk
  611  sudo fdisk -l < = = crucial and useful discoverer 
  612  lsblk | grep sdb
  613* lsblk  
  614  lsblk | grep sd
  615  lsblk -s
  616  lsblk -sa
  617  sudo blkid
  618  lsblk
  619  lsusb
  620  dmesg | grep -i usb
  621  sudo dmesg | grep -i usb
  622  sudo dmesg | grep -i clip
  623  sudo dmesg | grep -i sandisk
  624* sudo dmesg | gr
  625  sudo dmesg | grep -i manufacturer | wc
  626  sudo dmesg | grep -i manufacturer 
```
   
## Useful when mounting my two external backup drives 
```
 4272  sudo fdisk -l
 4273  sudo mkdir -p /mnt/externalbackupsmall
 4281  which ntfs-3g
 4279  sudo apt install ntfs-3g
 4282  sudo ntfsfix /dev/sda1
 4283  sudo mount -t ntfs-3g /dev/sda1 /mnt/externalbackupsmall/
 4291  sudo mkdir /mnt/externalbackuplarge
 4293  sudo ntfsfix /dev/sdb1
 4297  sudo umount  /dev/sda1 
 4298  sudo umount /dev/sdb1
```

or 

```
$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
$ sudo mkdir /media/yvan/four_TB/
$ sudo mount -t ntfs-3g /dev/sda1 /media/yvan/four_TB/
```
