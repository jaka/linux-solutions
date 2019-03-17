## disks

### Actions

#### Removing SATA disk
A device name of `/dev/sdc` is assumed.

Firstly find out controller the device is attached to (we'll need this later).
```
readlink /sys/block/sdc
```
We are now looking at the output for `hostX`. In next example it is `host2`.
```
../devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sdc
```
Disconnect the device
```
echo 1 > /sys/block/sdc/device/delete
```
Rescan the controller
```
echo "- - -" > /sys/class/scsi_host/host2/scan
```
