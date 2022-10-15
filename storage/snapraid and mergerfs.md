# Install deps
```doas apt update && doas apt upgrade && doas apt install nfs-server samba fuse mergerfs gcc make gdisk```

# Format drives
```doas gdisk /dev/sda
doas gdisk /dev/sdb
doas gdisk /dev/sdc
doas gdisk /dev/sdd
doas gdisk /dev/sde```

GPT fdisk (gdisk) version 1.0.6
Command (? for help): o
Proceed? (Y/N): y
Command (? for help): n
Command (? for help): w
Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
The operation has completed successfully.```

# Make filesystem
```doas mkfs.ext4 /dev/sda1
doas mkfs.ext4 /dev/sdb1
doas mkfs.ext4 /dev/sdc1
doas mkfs.ext4 /dev/sdd1
doas mkfs.ext4 /dev/sde1```

# Find drives by UUID
```sudo lsblk --output NAME,FSTYPE,LABEL,UUID,MODE```
