---
layout: post
title: Reformat EXFAT microSD card as FAT32
---

Naturally, Microsoft **patented** the EXFAT filesystem.  Thus, a new microSD card **will not work** on Linux or any other open source system, because they legally forbade it, and they had the muscle to make hardware vendors adopt EXFAT.  There exist unofficial tools, but another alternative is to just reformat using the older FAT32 filesystem, to avoid the issue, as follows: 

Use fdisk or your favorite partition editor to change the partition type to FAT32:

```
# fdisk /dev/whatever
Command (m for help): t
Selected partition 1
Hex code (type L to list all codes): b
Changed type of partition 'Linux' to 'W95 FAT32'.

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.
```

Then format:

```
# mkfs.vfat /dev/sde1
```

One day I suppose such workarounds will no longer be available.  Hopefully by that time, the world will have grown up a bit.
