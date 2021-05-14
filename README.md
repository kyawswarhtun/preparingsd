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

CMDline.txt 

dwc_otg.lpm_enable=0 console=serial0,115200 console=ttyS0 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait

Config.txt

kernel=kernel_rpilinux.img

arm_64bit=1

enable_uart=1

$ cp bcm2711-rpi-4-b.dtb /media/BOOT/

$ cp Image /media/BOOT/kernel_rpilinux.img

$ cd /media/ROOT/

$ sudo tar -xjf ~/Yocto/poky/build/tmp/deploy/images/{$image_name}/{$image_name}.tar.bz2

etc/fstab 

proc                    /proc           proc    defaults          0       0

/dev/mmcblk0p1          /boot           vfat    defaults          0       2

/dev/mmcblo0p2          /               ext4    defaults,noatime  0       1


