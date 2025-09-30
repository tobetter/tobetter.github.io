# Kernel message through UART debugging port

By default, kernel message through UART debugging port is disabled since
removing kernel message reduce the boot time a bit and most regular user do
not have UART debugging port.

## Fix up the booting parameters

1. Uncomment the line where **ttyAML0,115200n8** is specified from the file
   **/usr/share/flash-kernel/ubootenv.d/upstream/10-console**. This line
   will enable the UART debugging port for the kernel message.
```bash
$ cat /usr/share/flash-kernel/ubootenv.d/upstream/10-console
# Default serial console
# setenv console "ttyAML0,115200n8"
\
# Default TTY console
setenv bootargs "${bootargs} console=tty1"
```

1. Remove **quiet** from the file **/etc/default/flash-kernel**.
```bash
$ cat /etc/default/flash-kernel\
LINUX_KERNEL_CMDLINE="root=UUID=6322eafd-5b4c-474d-83ee-77c7223ccbd9 rootwait ro quiet splash"\
LINUX_KERNEL_CMDLINE_DEFAULTS=""
```

1. In order to apply the change to the boot script, run **update-bootscript**.
```bash
$ sudo /usr/sbin/update-bootscript
```
