# Custom Linux kernel

This page introduce how you can build the Linux kernel by yourself.

Linux kernel source is provided through Github repository and updated whenever
new kernel package is released. In order to build the Linux kernel, you must
download its kernel source using 'git' command and switch to the decent branch
which you are willing to build.

## Prerequisites
### Package requirements
In order to build Linux kernel, you need to install developement packages
required.
```bash
$ sudo apt install git build-essential bc flex bison libssl-dev libncurses-dev
```

### Download the Source code
```bash
$ git clone --depth 1 https://github.com/tobetter/linux \
-b `uname -r | awk -F'.' '{print "odroid-" $1 "." $2 ".y"}'`
```

## Compile your custom kernel
Unline the generic desktop, your Ubuntu/Debian uses a package **flash-kernel**
that helps to install the Linux kernel packages and the device tree file for a
target device. You have to tweak a couple of things once in order to let the
package **flash-kernel** install your custom kernel properly.

### Compile
> :warning: Use these commands once before preceeding.
```bash
$ cp /boot/config-$(uname -r) .config
$ sed -i "s/.*CONFIG_LOCALVERSION_AUTO.*/CONFIG_LOCALVERSION_AUTO=y/g" .config
$ echo "-odroid-arm64" > .scmversion
```
Then, start to compile the Linux kernel source.
```bash
$ make oldconfig
$ make -j8
```

### Install
> :warning: Use these commands once before preceeding.
```bash
$ sudo sed -i "s/^force=.*$/force=\"yes\"/g" /usr/share/flash-kernel/functions
$ sudo ln -s $PWD/arch/arm64/boot/dts /usr/lib/linux-image-$(cat include/config/kernel.release)
```
Then, you can install the Linux kernel image and its drivers. The boot script,
the device tree file and initramfs will be updated while installing by the
**flash-kernel**. Please note that your Linux kernel version must ends with
**-odroid-arm64**, so ensure the last log with **make modules_install**.
```bash
$ sudo make modules_install
$ sudo make install
```

For example,
```bash
$ sudo make modules_install
...
DEPMOD  5.9.15-odroid-arm64
$ sudo make install
sh ./arch/arm64/boot/install.sh 5.9.15-odroid-arm64 \
arch/arm64/boot/Image System.map "/boot"
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 5.9.15-odroid-arm64 /boot/vmlinuz-5.9.15-odroid-arm64
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 5.9.15-odroid-arm64 /boot/vmlinuz-5.9.15-odroid-arm64
update-initramfs: Generating /boot/initrd.img-5.9.15-odroid-arm64
Using DTB: amlogic/meson64_odroidn2_plus.dtb
Installing amlogic into /boot/dtbs/5.9.15-odroid-arm64/amlogic/
Installing amlogic into /boot/dtbs/5.9.15-odroid-arm64/amlogic/
flash-kernel: installing version 5.9.15-odroid-arm64
Generating boot script u-boot image... done.
Taking backup of boot.scr.
Installing new boot.scr.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 5.9.15-odroid-arm64 /boot/vmlinuz-5.9.15-odroid-arm64
run-parts: executing /etc/kernel/postinst.d/update-notifier 5.9.15-odroid-arm64 /boot/vmlinuz-5.9.15-odroid-arm64
run-parts: executing /etc/kernel/postinst.d/zz-flash-kernel 5.9.15-odroid-arm64 /boot/vmlinuz-5.9.15-odroid-arm64
Using DTB: amlogic/meson64_odroidn2_plus.dtb
Installing amlogic into /boot/dtbs/5.9.15-odroid-arm64/amlogic/
Installing amlogic into /boot/dtbs/5.9.15-odroid-arm64/amlogic/
flash-kernel: installing version 5.9.15-odroid-arm64
Generating boot script u-boot image... done.
Taking backup of boot.scr.
Installing new boot.scr.
```

## Tips
### Back up **/boot/boot.scr**
Installing your custom Linux kernel will update the boot script with the
version of your custom Linux kernel. It's good idea to back up the boot
script **/boot/boot.scr** to other file name and revert it when your
custom Linux kernel boot is failed.

### Multiple kernel versions
Your custom kernel won't overwrite the Linux kernel files installed with
packages. So after installing your custom Linux kernel image, there would be
multiple Linux kernel files in **/boot** directory and they can be listed with
the command **linux-version list**.
```bash
$ linux-version list
5.9.0-odroid-arm64
5.9.15-odroid-arm64
```

### Switching the kernel version
Suppose that you are running your custom kernel, but you want to switch to
the Linux kernel version installed with a kernel which is presented as
**5.9.0-odroid-arm64**, you can simply switch with **flash-kernel** with
a specific kernel version.
```bash
$ sudo flash-kernel --force 5.9.0-odroid-arm64
```
