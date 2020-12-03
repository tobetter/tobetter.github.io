# Temperature & Cooling fan control

## Need a tool to read temperature
In order to read the temperatures of CPU, new package **lm-sensors** must be installed.

```bash
$ sudo apt update
$ sudo apt install lm-sensors
$ sensors
```

## Temperature
The temperature of CPU can be read the command 'sensors'.
```bash
```

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
