## disks

### Actions

#### Remove a SATA disk
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
Remove the disk.

Rescan the controller
```
echo "- - -" > /sys/class/scsi_host/host2/scan
```

#### Create thin provisioned qcow2 disk image

This creates 60 GB disk image as file `/opt/test.qcow2`. Underlying filesystem must support thin provisioning.
```
qemu-img create -f qcow2 -o preallocation=metadata /opt/test.qcow2 60G
```
