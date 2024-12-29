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

## Logical Volumes
Logical volumes are volumes you can create logically, without the need to worry about physical disk size. With this, it's possible to make a 200 GB logical volume out of two 100 GB drives.
## Creating a logical volume
To create a 10 GB home partition out of `MyVolGroup`, then make it available, invoke the following commands:
```
# Create a 10 GB partition
lvcreate --size 10G --name home MyVolGroup
mkfs.ext4 /dev/MyVolGroup/home

# Create a partition to cover the rest of the free space
lvcreate --extents 100%FREE --name home MyVolGroup
mkfs.ext4 /dev/MyVolGroup/home
```
The first command creates a 10 GB logical volume, then the second formats it to make it useable.
### Specifying volume sizes
There are two ways to specify LV sizes on creation.
* `--size or -L` allows specifying a hard-coded size. Useful for allocating an exact size for a partition. As an example, the command listed above shows how to create a 10 GB partition off of `MyVolGroup`.
*  `--extents or -l` allows specifying size based on percentage. For example, `lvcreate --extents 100%FREE --name home MyVolGroup` creates a `home` partition with the remaining free space `MyVolGroup` has.