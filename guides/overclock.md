# CPU/GPU frequency and governor
> :warning: The commands in this section only affects to the product with S905X3 and
S922X.

## CPU
The min/max CPU frequency and governor can be changed by editing
'/etc/default/cpufrequtils' and it will be applied from next booting.

```bash
$ cat /etc/default/cpufrequtils
GOVERNOR=performance
MIN_SPEED="1000MHZ"
MAX_SPEED="2016MHZ"
```

The change in '/etc/default/cpufrequtils' will affect to big.LITTLE cores at
the same time and will use the most closet value if given freqency does not
exist. Valid frequencies are able to check with this command.
```bash
$ cat /sys/devices/system/cpu/cpufreq/policy0/scaling_available_frequencies
$ cat /sys/devices/system/cpu/cpufreq/policy2/scaling_available_frequencies
```

### Overclocking

CPU overclock can happen if you change the value of 'MAX_SPEED' in
/etc/defaults/cpufrequtils but could lead malfunction or shutdown
unexpected since they are not officially supported by SoC vendor.
The feasible freqencies varies to the CPU.

#### ODROID-N2 ####
* 1908MHz
* 2004MHz

#### ODROID-N2Plus ####
* 2304MHz
* 2400MHz

#### ODROID-C4/HC4 ####
* 2016MHz
* 2100MHz

## GPU

The min/max GPU frequency and governor can be changed by editing
'/etc/default/gpufrequtils' and it will be applied from next booting.

> :warning: The commands in this section only after Linux kernel 5.10.16.

```bash
$ uname -a
Linux focal-server 5.10.0-odroid-arm64 #1 SMP PREEMPT Ubuntu 5.10.16-202102191318~groovy (2021-02-19) aarch64 aarch64 aarch64 GNU/Linux
```

```bash
$ cat /etc/default/gpufrequtils
# GOVERNORS:    [userspace powersave performance simple_ondemand]
# FREQUENCIES : [124999998 249999996 285714281 399999994
#                499999992 666666656 799999987]
GOVERNOR=performance
MIN_FREQ=499999992
MAX_FREQ=799999987
```
The change in '/etc/default/gpufrequtils' will affect to GPU and will use the
most closest value if given frequency does not exist. Valid frequencies are
able to check with this command.

#### With Mali Bifrost driver
<ul>
<li>/sys/devices/platform/soc/ffe40000.gpu/misc/mali0/device/devfreq/ffe40000.gpu/governor</li>
<li>/sys/devices/platform/soc/ffe40000.gpu/misc/mali0/device/devfreq/ffe40000.gpu/min_freq</li>
<li>/sys/devices/platform/soc/ffe40000.gpu/misc/mali0/device/devfreq/ffe40000.gpu/max_freq</li>
</ul>

#### With Mali Panfrost driver
<ul>
<li>/sys/devices/platform/soc/ffe40000.gpu/devfreq/ffe40000.gpu/governor</li>
<li>/sys/devices/platform/soc/ffe40000.gpu/devfreq/ffe40000.gpu/max_freq</li>
<li>/sys/devices/platform/soc/ffe40000.gpu/devfreq/ffe40000.gpu/min_freq</li>
</ul>

### Overclocking

GPU overclock can happen if you change the value of 'MAX_SPEED' in
/etc/defaults/gpufrequtils but could lead malfunction or shutdown
unexpected since they are not officially supported by SoC vendor.
The fasible frequency for overclocking is only 1000MHz.

```bash
MAX_FREQ=1000000000
```
