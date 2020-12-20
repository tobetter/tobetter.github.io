# Prebuilt OS Image

This is the legacy and general mothod that most SBC vendors and OS developer groups provide. Basically a user download the OS image uploaded to a storage server of OS image provider and flash the image to SD or eMMC memory card using a couple of flashing tools. Then a user only need to insert the memory card to SBC and boot from it directly, this is most easist way if user is not borthered to change the OS setup.

For this method, only server image is provided at the momenty while Hardkernel provides two type of images - **Minimal** and **Ubuntu Mate Desktop**. The server image is to offer the bare minimal Debian/Ubuntu OS with console mode, t can be extended to a desktop OS with GUI after installing a desktop meta package such as Gnome Desktop or KDE Destip. The server image will be released for several ODROID SBC as different file image files. Please visit the links for your ODROID SBC to download the image.

* [ODROID-N2/N2Plus](odroidn2/image.md)
* [ODROID-C4](odroidc4/image.md)
* [ODROID-HC4](odroidhc4/image.md)

## See also
* [Balena Etcher](https://www.balena.io/etcher/)
* [Custom Etcher for ODROID](https://forum.odroid.com/viewtopic.php?f=55&t=40411)
