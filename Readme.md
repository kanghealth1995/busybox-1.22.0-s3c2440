
# Readme

make ARCH=arm CROSS_COMPILE=arm-linux- menuconfig

    CONFIG_STATIC=y

    CONFIG_CROSS_COMPILER_PREFIX="arm-linux- menuconfig-"

make -j8

make install

cp rootfs/* _install -dr

## yaffs2 

tar -jxvf yaffs_source_util_larger_small_page_nand.tar.bz2

cd utils

make

mkyaffs2image _install/   rootfs.yaffs2
