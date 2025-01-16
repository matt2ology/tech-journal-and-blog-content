---
authors: David Duarte
categories:
date: 2025-01-16
draft: true
source-url: https://www.howtoforge.com/tutorial/mount-ntfs-centos/
mediums: articles
notes: reference
tags: readwise, reference/articles
title: Reference - How to Mount an NTFS Drive on CentOS / RHEL / Rocky Linux
---
## How to Mount an NTFS Drive on CentOS / RHEL / Rocky Linux

![rw-book-cover](https://www.howtoforge.com/images/featured/rhel-ntfs.jpg)

published-date: None

**Link:** [How to Mount an NTFS Drive on CentOS / RHEL / Rocky Linux](https://www.howtoforge.com/tutorial/mount-ntfs-centos/)

## Highlights
### id659039576

> yum install epel-release
> \- [(View Highlight)](https://read.readwise.io/read/01hkxnjx1xxqbpx5y974n621ah)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01hkxnjx1xxqbpx5y974n621ah)
Enables the Extra Packages for Enterprise Linux (EPEL), a Fedora Special Interest Group that creates, maintains, and manages additional packages for Enterprise Linux distributions like Red Hat Enterprise Linux (RHEL), CentOS, Scientific Linux (SL), and Oracle Linux (OL).

### id659039887

> yum install ntfs-3g
> \- [(View Highlight)](https://read.readwise.io/read/01hkxnqwdjr6zefa8y1m15g7sy)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01hkxnqwdjr6zefa8y1m15g7sy)
This installs the `ntfs3` file system packages, so to allow users to use drives that are formatted with Microsoft's New Technology File System (NTFS).

### id659150508

> mkdir /mnt/win
> \- [(View Highlight)](https://read.readwise.io/read/01hky8x3nkrfkmevkcpzeqdc51)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01hky8x3nkrfkmevkcpzeqdc51)
After installing the windows New Technology File System (NTFS) drive a directory can be created where it can be mounted. In full, after the directory has been created (i.e. the mounting point), the NTFS partition can be mounted like so: `mount -t ntfs-3g /dev/sdb1 /mnt/win`
In this example, my NTFS partition is the device /dev/sdb1. You have to replace that with the device name of your NTFS partition.
However the above is temporary. For a permanent solution one would need to edit `/etc/fstab` and append the following line `/dev/sdb1 /mnt/win ntfs-3g defaults 0 0`
Where `/dev/sdb1` is the device name of your NTFS partition.



