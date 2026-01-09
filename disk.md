List block devices
```sh
lsblk
```

Output info about filesystems.
```sh
lsblk -f [device...]
```

Displays the amount of space available on the file system containing each file name argument. If no file name is given, the space available on all currently mounted file systems is shown.
```sh
df -h [FILE]
```

List the partition tables for the specified devices and then exit.  If no devices are given, the devices mentioned in /proc/partitions (if this file exists) are used.
```sh
fdisk -l [device...]
```
Manipulate disk partition table (m for help)
```
fdisk [device]
```

> Create a new label
> - g  create a new empty GPT partition table
> - o  create a new empty MBR (DOS) partition table

> Generic
> - p  print the partition table
> - n  add a new partition
> - t  change a partition type (type L to list all)
> - d  delete a partition

| num | alias | type             |
| --- | ----- | ---------------- |
| 1   | uefi  | EFI System       |
| 20  | linux | Linux filesystem |
| 19  | swap  | Linux swap       |
| 42  | home  | Linux home       |
| 44  | lvm   | Linux LVM        |

> DOS (MBR)
> - a  toggle a bootable flag

> MBR disk partition table sample (extended ≤ 1, primary + extended ≤ 4, extended cotains logical up to 128).
> After add a extended partition using all the remain space, it sometimes remind that **"All space for primary partitions is in use."** without showing **"Adding logical partition"** option when add a new partition as ioctl() delay re-reading altered partition table to sync disks. Just use `w` to write table to disk and exit, then re-enter into fdisk.

| Device    | Boot | Start     | End       | Sectors   | Size | Id   | Type            |
| :-------- | ---- | --------: | --------: | --------: | ---: | ---: | :-------------- |
| /dev/sda1 | *    | 2048      | 2099199   | 2097152   | 1G   | 83   | Linux           |
| /dev/sda2 |      | 2099200   | 268435455 | 266336256 | 127G | f    | W95 Ext'd (LBA) |
| /dev/sda5 |      | 2101248   | 268435455 | 266334208 | 127G | 8e   | Linux LVM       |

> Save & Exit
> - w  write table to disk and exit
> - q  quit without saving changes
