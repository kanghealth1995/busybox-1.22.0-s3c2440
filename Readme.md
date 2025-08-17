
# Readme

make ARCH=arm CROSS_COMPILE=arm-linux- menuconfig

    CONFIG_STATIC=y

    CONFIG_CROSS_COMPILER_PREFIX="arm-linux- menuconfig-"

make -j8

make install


cd _install

mkdir -p lib usr/lib etc dev home sys proc tmp mnt

cp /usr/local/arm/4.3.2/arm-none-linux-gnueabi/libc/armv4t/lib/*so*  lib/ -d

cp /usr/local/arm/4.3.2/arm-none-linux-gnueabi/libc/armv4t/usr/lib/*so*  usr/lib/ -d

fstable:

    # device     mount-point    type   options        dump  fsck order

    proc           /proc        proc   defaults        0     0

    tmpfs          /tmp         tmpfs  defaults        0     0

    sysfs          /sys         sysfs  defaults        0     0

    tmpfs          /dev         tmpfs  defaults        0     0

inittab:

    # /etc/inittab

    ::sysinit:/etc/init.d/rcS

    console::askfirst:-/bin/sh

    ::ctrlaltdel:/sbin/reboot

    ::shutdown:/bin/umount -a -r



## yaffs2 

tar -jxvf yaffs_source_util_larger_small_page_nand.tar.bz2

cd utils

make

mkyaffs2image _install/   rootfs.yaffs2
