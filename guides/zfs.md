# The Z File System (ZFS)

><span style="color:red">The command in this page has been tested with 5.7 kernel only, not with 5.8 and later. Please let us know if you have success with newer kernel version</span>

## Background
Instead of installing the **zfs-dkms** package, I've tried to build the latest version 0.8.4 from Github and zfs*.ko can be built with these commands. I've not tested if zfs work or not, so please do at your own risk.

## Check kernel version

```bash
$ uname -a
Linux ubuntu 5.7.0-odroid-arm64 #1 SMP PREEMPT Ubuntu 5.7.2-202006130259~focal (2020-06-12) aarch64 aarch64 aarch64 GNU/Linux
```

## Install
```bash
$ sudo apt purge zfs-dkms libzfs2linux zfs-zed zfsutils-linux
$ sudo apt install autoconf automake libtool zlib1g-dev uuid-dev libblkid-dev libssl-dev
$ wget https://github.com/openzfs/zfs/archive/zfs-0.8.4.tar.gz
$ tar xzvf zfs-0.8.4.tar.gz
$ cd zfs-zfs-0.8.4
$ ./configure --prefix=/usr
$ make
$ sudo make install
```
