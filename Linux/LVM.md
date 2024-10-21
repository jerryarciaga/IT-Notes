LVM is a device mapper framework that provides logical volume management for the Linux kernel.

# Setup LVM
## Physical volumes
First, you set up physical volumes by "marking" whole disks or partitions as a physical volume, like so:
```
pvcreate /dev/sda1
```
You can then use `pvdisplay` to display block devices set as physical volumes.
## Volume groups
### Create volume groups
After setting up physical volumes, you create volume groups to merge these physical volumes together. You do this by running:
```
vgcreate MyVolGroup /dev/sdb1
```
The command above creates a volume group with an associated physical volume `/dev/sdb1`. You can check the status of your newly created volume group by invoking `vgs`.
### Activate volume groups
Activate volume groups by invoking the following as `root`.
```
vgchange -a y MyVolGroup
```
