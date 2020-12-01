---
sort: 99
---

# FAQ

#### Why only 'server' images are provided, not 'desktop'?
The server image is smaller than the desktop image and can be extended from. The desktop installation can be done with a couple of commands when your ODROID is connected to the network. Personally using Netboot Installer is highly recommended.

#### What's 'unofficial' Netboot Installer?
Debian and Ubuntu already provide the Netboot Installer but their Netboot Installer does not support all packages that require to run ODROID since the default kernel package and certain packages do not have any type of code or scripts. So the Netboot Installer from the official server won't work on ODROID and installation will fail due to lack of hardware support packages. So the **unofficial** Netboot Installer is the customized version of the official Netboot Installer to provide the packages for ODROID.

#### Where do the packages are from?
In order to provide ODROID specific features with the provided OS, a private package archive server is running - https://ppa.linuxfactory.or.kr - and this server provides the customized packages for ODROID only.

{% include list.liquid %}
