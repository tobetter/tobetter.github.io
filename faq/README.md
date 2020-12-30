---
sort: 99
---

# FAQ

#### Why only 'server' images are provided and not 'desktop' ones?
The server image is smaller than the desktop image and can be easily customized to your needs. The desktop installation can be done with a couple of commands when your ODROID is connected to the network. Personally using Netboot Installer is highly recommended. 
You can get a list of supported desktop environments with:
``` 
# sudo apt-cache search ubuntu*-desktop
ubuntu-desktop - The Ubuntu desktop system
ubuntu-desktop-minimal - The Ubuntu desktop minimal system
kubuntu-desktop - Kubuntu Plasma Desktop/Netbook system
lubuntu-desktop - Lubuntu Desktop environment
xubuntu-desktop - Xubuntu desktop system
```
You can install the desired desktop with:
```
# sudo apt-get install ubuntu-gnome-desktop
```

#### What's 'unofficial' Netboot Installer?
Debian and Ubuntu already provide the Netboot Installer but their Netboot Installer does not support all packages that require to run ODROID since the default kernel package and certain packages do not have any type of code or scripts. So, the Netboot Installer from the official server won't work on an ODROID and installation will fail due to lack of hardware support packages. So the **unofficial** Netboot Installer is the customized version of the official Netboot Installer to provide the packages for ODROID.

#### Where do the packages are from?
In order to provide ODROID specific features with the provided OS, a private package archive server is running from - https://ppa.linuxfactory.or.kr - and this server provides the customized packages for ODROID only.

#### mali-bifrost-wayland-driver : Depends: mali-bifrost-dkms but it is not installable ####
To fix this (happens with the 20201218 image), please run the commands below
```
echo 'deb http://ppa.linuxfactory.or.kr focal contrib' > /etc/apt/sources.list.d/ppa_linuxfactory_or_kr.list
apt-get update
apt-get install mali-bifrost-wayland-driver
```
And reboot afterwards.

{% include list.liquid %}
