---
title: Mount External Driver in Raspberrypi 4
author: Yan Zhang
date: 2020-08-02 10:55:00 +0800
categories: [Tutorial]
tags: [Python]
pin: true
---

## Umount External Driver

```python
sudo umount -t hfsplus  /mnt/old_media_folder
sudo rmdir /mnt/old_media_folder
```


## Mount External Driver

```python
sudo fdisk -l

sudo mkdir /mnt/new_media_folder

sudo fsck.hfsplus /dev/sda3

sudo mount -t hfsplus -o force,rw /dev/sda3 /mnt/new_media_folder
```
