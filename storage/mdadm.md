## Install deps
```doas apt update && doas apt upgrade && doas apt install nfs-server samba gdisk mdadm```

## Format drives (only needed once but I'll keep it here since I will probably add drives at some point)
```doas gdisk /dev/sda
doas gdisk /dev/sdb
doas gdisk /dev/sdc
doas gdisk /dev/sdd
doas gdisk /dev/sde

GPT fdisk (gdisk) version 1.0.6
Command (? for help): o
Proceed? (Y/N): y
Command (? for help): n
Command (? for help): w
Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
The operation has completed successfully.

doas mkdir /mnt/{mirror,parity}

mdadm --create --verbose /dev/raid5 --level=5 --raid-devices=3 /dev/sda /dev/sdc /dev/sde
mdadm --create --verbose /dev/md1 --level=1 --raid-devices=2 /dev/sdb /dev/sdd

mdadm --detail --scan --verbose | tee -a /etc/mdadm/mdadm.conf

doas mount /dev/md1 /mnt/mirror
doas mount /dev/md5 /mnt/parity
