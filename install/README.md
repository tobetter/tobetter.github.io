# Debian/Ubuntu Installation

## Methods
We provide two methods of OS installation and the default Linux kernel version with the OS with the installation guide in this document is the mainline Linux kernel 5.9 or later. Also supported method of OS installation or the Linux kernel version could be various to a specific ODROID SBC.

### [Prebuilt OS image](prebuilt_image.md)
This is most generic method of installing OS to SBC today, SBC vendor or OS developer team provide the complete image file that can be flashed to a memory card - SD or eMMC. The OS image file can be flahed with the [balenaEther](https://www.balena.io/etcher/) on your PC after downloading the image file.

### [Netboot Installer](netboot_installer.md)
This is very simliar to generic Linux OS installation to your PC. The Netboot Installer is provided for Ubuntu/Debian Linux systems and the installer is customized from original Netboot Installer of Ubuntu/Debian Linux. The advantage of using Netboot Installer is that user can customize their OS set up a bit more than **Prebuilt OS image** and all the packages will be updated while updating whilise your ODROID must be connected to the network while installing.
