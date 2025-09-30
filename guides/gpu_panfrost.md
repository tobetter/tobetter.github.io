# GPU Acceleration with ARM Mali Panfrost

Panfrost is a free and open source driver for Mali Midgard and Bifrost GPU and public code hosting is on GitLab. For ODROID, this GPU acceleration driver is only supported with the Linux kernel 5.10 and later. Since the Panfrost driver is still experimental driver and being updated by the developers, the features and its stability will be greatly improved.
><span style="color:red">Panfrost and Bifrost driver must not be loaded together in the same system.</span>

## Showcase
> Ubuntu 20.10 KDE Desktop with ARM Mali Panfrost driver
<iframe width="560" height="315" src="https://www.youtube.com/embed/I2EzbDVGH4w" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Install
Panfrost driver is is provided with the kernel package, therefore no additional commands are not required other than kernel package update.

```bash
$ sudo apt update
$ sudo apt dist-upgrade
```

## Check if Mali Panfrost driver is loaded
Panfrost is provided as the Linux kernel dirver module, the driver **panfrost.ko** must be loaded after rebooting.
```bash
$ lsmod | grep panfrost
panfrost              69632  0
```

## Test with Mali Panfrost driver
The **glmark2** is a good utility to test GPU performance.
```bash
$ sudo apt update
$ sudo apt install glmark2
$ glmark2
```

## See also
[1] https://panfrost.freedesktop.org/
