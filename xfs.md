# XFS Commands 

### Mount Drive with duplicate UUID
$ sudo mount -o rw,nouuid /dev/sda3  /mnt

### Give drive new UUID
$ sudo xfs_admin -U generate /dev/sda3
