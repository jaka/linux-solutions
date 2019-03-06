## partitions

### Actions

#### View partition tables
```
fdisk -l 
```

#### Backup Master Boot Record (MBR)
```
$ dd if=/dev/sdb of=my.mbr bs=466 count=1
```
where `my.mbr` is a file where we would like to store our MBR.

#### Restore Master Boot Record (MBR) from a file
Just switch the order of input and output files.
```
$ dd if=my.mbr of=/dev/sdb bs=466 count=1
```

#### Destroy Master Boot Record (MBR)

As a input file use `/dev/zero`.
```
$ dd if=/dev/zero of=/dev/sdb bs=466 count=1
```
