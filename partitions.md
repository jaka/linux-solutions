## Partitions

### Actions

#### Backup NTFS partition with compression
```
partclone.ntfs -c -s /dev/sda1 | gzip -c -3 > ./part1.gz
```

#### Mount NTFS read-only for all users
Append the following options to `mount`
```
fmask=0133,dmask=0022
```

### Partition tables
Always double check name of drive block device!

#### View partition tables
```
fdisk -l
```

#### Backup Master Boot Record (MBR)
```
$ dd bs=466 count=1 if=/dev/sdb of=my.mbr
```
where `my.mbr` is a file where we would like to store our MBR and `/dev/sdb` drive.

#### Restore Master Boot Record (MBR) from a file
Just switch the order of input and output files.
```
$ dd bs=466 count=1 if=my.mbr of=/dev/sdb
```

#### Destroy Master Boot Record (MBR)

As a input file use `/dev/zero`.
```
$ dd bs=466 count=1 if=/dev/zero of=/dev/sdb
```

#### Remove MRB and partition table (classic DOS PT)
```
$ dd bs=512 count=1 if=/dev/zero of=/dev/sdb
```

#### Apply syslinux MBR to a disk
```
$ dd bs=440 count=1 conv=notrunc if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sdb
```
