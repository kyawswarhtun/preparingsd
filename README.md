# preparingsd
$ sudo fdisk -l
$ sudo umount /dev/sdb1
$ sudo umount /dev/sdb2

$ sudo parted -s /dev/sdb \
mklabel msdos \
mkpart primary fat32 1M 100M \
mkpart primary ext4 100M 100%

$ sudo mkfs.vfat /dev/sdb1
$ sudo mkfs.ext4 /dev/sdb2

$ sudo fatlabel /dev/sdb1 BOOT
$ sudo e2label /dev/sdb2 ROOT

$ sudo mount /dev/sdb1 /media/BOOT
$ sudo mount /dev/sdb2 /media/ROOT

