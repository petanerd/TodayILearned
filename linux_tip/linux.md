# TIL linux

## code snippet

```shell
# disk mount wokring process
$ su
$ fdisk -l
$ mount /dev/sdbx /mount/point
$ df -h

# disk mount permanent

# UUID information
$ blkid
# disk information (include UUID)
$ file -sL /dev/sd*
# write information on /etc/fstab
$ vi /etc/fstab
#
# /etc/fstab
# Created by anaconda on Sun Feb 14 21:38:44 2016
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
# / was on /dev/sda2 during installation
UUID=a3f55391-671f-45c3-9b1c-a98525479bfa /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=9F03-FAC2  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=9da91f71-0c44-469f-96b0-55ca04f3c173 none            swap    sw              0       0

# sdb1 /data --> add new disk
UUID=94b2eb62-df37-11e8-a2ce-2c4d54459d4c /data ext4    defaults        1 2

```

```shell
# view file size as Mb when type ls -l
ls -l --block-size=M
```
