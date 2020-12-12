# 'Authentication Required' when open the network setting

## Problem
>This error is reported with Linux 5.10 on Ubuntu 20.10, a dialog box pop-up with ***Authentication Required*** and request password but actually cannot change the network settings whilist the network is working.

![forum](https://forum.odroid.com/download/file.php?id=12942)

## Workaround
By adding or modifying the file **/etc/netplan/50-cloud-init.yaml**, the menu is changed to 'Wired Connected' from 'Wired Unamaged' after rebooting.
```
network:
  renderer: NetworkManager
  ethernets:
    eth0:
      dhcp4: true
  version: 2
```

## See also
https://askubuntu.com/questions/1039233/no-wired-connection-wired-unmanaged-ubuntu-18-04
https://askubuntu.com/questions/1267212/ethernet-connection-not-working-on-ubuntu-20-04
