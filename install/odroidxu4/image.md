# ODROID-XU4/HC1/HC2

>:warning: The default account is 'odroid' and its password is 'odroid', please do change the password at the first boot.

## Debian 9 (Buster)
* [20210119](http://ppa.linuxfactory.or.kr/images/raw/armhf/debian-buster-server-odroidxu4-20210119.img.xz) - Linux kernel v5.10

## Ubuntu 20.04
* [20210118](http://ppa.linuxfactory.or.kr/images/raw/armhf/ubuntu-20.04-server-odroidxu4-20210118.img.xz) - Linux kernel v5.10
* [20210111](http://ppa.linuxfactory.or.kr/images/raw/armhf/ubuntu-20.04-server-odroidxu4-20210111.img.xz) - Linux kernel v5.10

### Please do this before flashing the image to eMMC
* You need to replace the bootloader in the eMMC since the image can not boot from the Hardkernel stock U-boot, so please follow up the instructions.
1. Download and flash the [update image](http://ppa.linuxfactory.or.kr/images/raw/armhf/update_uboot-odroidxu4-20210111.img.xz) to SD card.
1. Attach your eMMC and SD card flash with the update image to your ODROID-XU4
1. Place the boot select switch to SD card
1. Power on, then update will start and turn off once the update is finished
1. Done
