List block devices
```sh
lsblk
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
>   ef uefi linux - 83
| num | alias | type             |
| --- | ----- | ---------------- |
| 1   | uefi  | EFI System       |
| 20  | linux | Linux filesystem |
| 19  | swap  | Linux swap       |
| 42  | home  | Linux home       |
| 44  | lvm   | Linux LVM        |

> - d  delete a partition

> Save & Exit
> - w  write table to disk and exit
> - q  quit without saving changes
