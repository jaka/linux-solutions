## mdadm (raid)

### Actions

#### Creating a RAID5 array from 4 raw disks
```
mdadm --create --verbose /dev/md/0 --level=raid5 --chunk=64K --raid-devices=4 --spare-devices=0 /dev/sd{a,b,c,d}
```
Save the array to configuration
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

#### Scrubbing the array
Check array `md0`
```
echo check > /sys/block/md0/md/sync_action
```

#### Removing a drive from MD
```
mdadm /dev/md0 --fail /dev/sdc
mdadm /dev/md0 --remove /dev/sdc
```
