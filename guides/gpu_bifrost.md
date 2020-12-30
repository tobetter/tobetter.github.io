# GPU Acceleration with ARM Mali Bifrost

Bifrost is the third generation of ARM Mali GPUs and its family includes the Mali-G30, Mali-G50 and Mali-G70 series of products. The ODROID with ARM Mali Bifrost are ODROID-N2/N2Plus/C4/HC4 based on Amlogic S905X3 and S922X. This page guide you to use the open source ARM Mali GPU driver with its user space driver blob which is the proprietary of ARM. The open source ARM Mali GPU driver is from [here](https://developer.arm.com/tools-and-software/graphics-and-gaming/mali-drivers/bifrost-kernel) and currently **BX301A01B-SW-99002-r23p0** has been ported to Linux kernel 5.7 and later. Since ARM Mali GPU driver is the proprietary of ARM, supported features are limited. Currently Mali **Wayland driver** has been tested and **X11 is not supported yet**.

## Showcase
> Ubuntu 20.04 Gnome Desktop with ARM Mali Bifrost

<iframe width="560" height="315" src="https://www.youtube.com/embed/J9EuXwxVik0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Install

The Bifrost driver is not provided along with Linux kernel package, but provided with individual package. The installation is quite simple but need some tweaks when it does not work after following the installation commands. And the driver works only after rebooting. At the moment, only Wayland backed ARM Mali Bifrost driver is available and verified. Therefore, a desktop environment with X11 would not.

```bash
$ sudo apt update
$ sudo apt dist-upgrade
$ sudo apt install mali-bifrost-wayland-driver
$ sudo reboot
```
## Check if Mali Bifrost driver is loaded
Bifrost driver is provided as the Linux kernel driver module, so the driver **malk_kbase.ko** must be loaded after rebooting.
```bash
$ lsmod | grep mali_kbase
mali_kbase            61440  0
```

## Test with Mali Bifrost driver
The **glmark2-es2-wayland** is the best benchmark tool since current Mali Bifrost driver suppports only Wayland userspace driver.
```bash
$ sudo apt update
$ sudo apt install glmark2-es2-wayland
$ glmark2-es2-wayland
```

## Uninstall
The installed Bifrost driver can be removed with **apt** but you need to be careful that this could corrupt your installed OS setup since this package could remove other dependency packages. **Uninstalling with this command could cause of removing more packages installed on your system**.

```bash
$ sudo apt purge mali-bifrost-wayland-driver mali-bifrost-dkms
$ sudo reboot
```

## Trouble shooting
### Cannot get login to Gnome Wayland Desktop, but X11 Desktop
Probably you didn't select **Gnome Wayland Session**
### 

### When ARM Mali Bifrost is not working
Probably this could happen after new kernel package is updated. In such case, ARM Mali Bifrost driver must be reinstalled properly.
```bash
$ sudo apt install --reinstall mali-bifrost-dkms
$ sudo reboot
```

### Error when install **mali-bifrost-dkms**
This error could be caused when the Linux header package is not installed, so highly recommend to install the package before installing Bifrost packages.
```bash
$ sudo apt install linux-headers-$(uname -r)
```
