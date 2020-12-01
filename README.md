# LinuxFactory

## Quick start
The document in this page provides instructions to install/update OS images and to help to use them for your purposes on ODROID SBC of Hardkernel. The commands in the documents would not be compatible or equivalent to the contents in the ODROID Wiki since the OS images provided through this page offer the Linux upstream kernel, its configuration and features are different.

## Method of OS installation
We offer two installation methods - prebuilt server image and Netboot Installer.The general way to provide OS image for SBC today is to provide the customized complete image file that can boot immediately once it's been flashed to memory card - eMMC or SD card. Unlike this, but like what we are doing with PC, 'unofficial' Netboot Installer is also provided.

#### Why only 'server' images are provided, not 'desktop'?
The server image is smaller than the desktop image and can be extended from. The desktop installation can be done with a couple of commands when your ODROID is connected to the network. Personally, I strongly recommend using the Netboot Installer for the first installation.

#### What's 'unofficial' Netboot Installer?
Debian and Ubuntu already provide the Netboot Installer but their Netboot Installer does not support all packages that require to run ODROID since the default kernel package and certain packages do not have any type of code or scripts. So the Netboot Installer from the official server won't work on ODROID and installation will fail due to lack of hardware support packages. So the **unofficial** Netboot Installer is the customized version of the official Netboot Installer to provide the packages for ODROID.

#### Where do the packages are from?
In order to provide ODROID specific features with the provided OS, a private package archive server is running - https://ppa.linuxfactory.or.kr - and this server provides the customized packages for ODROID only.
