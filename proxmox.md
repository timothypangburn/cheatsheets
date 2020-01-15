### Restore a VM from a Backup - override original
qmrestore /mnt/pve/proxmoxstore/dump/vzdump-qemu-306-2017_09_26-19_01_49.vma.gz 306 -storage castle-prod-p1 -force true

### Find missing hotplug memeory in VM
```
#!/bin/bash

for RAM in $(grep line /sys/devices/system/memory/*/state)
do
    echo "Found ram: ${RAM} ..."
    if [[ "${RAM}" == *":offline" ]]; then
        echo "Bringing online"
        echo $RAM | sed "s/:offline$//"|sed "s/^/echo online > /"|source /dev/stdin
    else
        echo "Already online"
    fi
done
```

