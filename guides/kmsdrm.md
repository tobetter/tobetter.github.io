# Kernel mode setting

Kernel mode setting (KMS) is a method to set the display resolution in the
Linux kernel during boot up, this method also effectly work when:
* you want to set the display mode with specific resolution
* the display device is old
* EDID data is corrupted or it contains incorrect one


## Prerequisites
### EDID binary

You need to download and install the EDID binary file to your Linux. Please open
the link to find out the supported EDID binaries.
https://github.com/akatrevorjay/edid-generator

Please run these commands to download the display resolution for 1920x1080.
```bash
$ sudo mkdir -p /usr/lib/firmware/edid/
$ sudo wget https://github.com/akatrevorjay/edid-generator/blob/master/1920x1080.bin -P /usr/lib/firmware/edid
```
## Apply new resolution
In order to apply the new display resolution with this method, the boot script
must be updated with a kernel parameter that specify the display resoltuion so that
the Linux kernel loads the EDID binary on booting.

Add this line to **/usr/share/flash-kernel/ubootenv.d/upstream/90-misc** to select the display resolution as 1920x1080.
> setenv bootargs "${bootargs} drm_kms_helper.edid_firmware=HDMI-A-1:edid/1920x1080.bin"

So, the file **/usr/share/flash-kernel/ubootenv.d/upstream/90-misc** must be like this.
```bash
$ cat /usr/share/flash-kernel/ubootenv.d/upstream/90-misc 
setenv bootargs "${bootargs} cma=800M"
setenv bootargs "${bootargs} clk_ignore_unused"
setenv bootargs "${bootargs} drm_kms_helper.edid_firmware=HDMI-A-1:edid/1920x1080.bin"
```

Then update the boot script to apply the change and reboot.
```bash
$ sudo update-bootscript
$ sudo reboot
```
