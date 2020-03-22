## kvm

### attach network
Add a network interface to a KVM guest named `n32` bridged to `br65` on host and make it permanent by writting to the config. 
```
virsh attach-interface n32 bridge br65 --model virtio --config
```
