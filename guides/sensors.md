# Sensors

## Background
In order to read the sensors on your board, new package **lm-sensors** must be installed.

```bash
$ sudo apt update
$ sudo apt install lm-sensors
```

## Read sensors
After installing the package 'lm-sensros', the sensors of your ODROID can be read with the command 'sensors'. This command will show the current temperatures provided by CPU itself. The fan speed also can be provided when cooling fan is attached only when it provides TACH signals.

```bash
$ sensors
pwmfan-isa-0000
Adapter: ISA adapter
Default Fan: 3017 RPM

cpu_thermal-virtual-0
Adapter: Virtual device
CPU Temp:     +37.7°C  (crit = +110.0°C)

ddr_thermal-virtual-0
Adapter: Virtual device
DDR Temp:     +39.0°C  (crit = +110.0°C)
```

![forum](https://forum.odroid.com/download/file.php?id=12919)

## Fanspeed control
Cooling fan speed can be controlled in 3 modes - Automatic/Manual/Maximum - and one needs to access sysfs node with granted permission since changing the fan speed can.

#### Automatic mode
The fan speed is set by Linux kernel as defined cooling point in the device tree, this is the default.
```bash
$ echo 2 | sudo tee /sys/class/hwmon/hwmon0/pwm1_enable
```

#### Manual mode
This mode is to set the fan speed manually by a user or a service in the userspace and predefined cooling point in the kernel space will be completely ignored. So mode could be harm if the fan speed is not properly managed whenever CPU temperature is changed. The range of fan speed is from 0 to 255 where 0 as turn off and 255 as maximum speed.

```bash
$ echo 1 | sudo tee /sys/class/hwmon/hwmon0/pwm1_enable
$ echo 128 | sudo tee /sys/class/hwmon/hwmon0/pwm1
```

#### Maximum mode
This mode is to set the fan speed at its maximum speed until the fan speed mode is changed to 'Automatic' or 'Manual'.

```bash
$ echo 0 | sudo tee /sys/class/hwmon/hwmon0/pwm1_enable
```

## Fanspeed control using 'fancontrol'

```bash
$ sudo apt update
$ sudo apt install fancontrol
```
