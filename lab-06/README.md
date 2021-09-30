# LAB 05 | PULSE-WIDTH-MODULATION (PWM)

## Theory

PWM has its average value proportional to the amplitude of the modulating signal, and it may be retrieved by using a low-pass filter.
Longer pulses in it represent the anti-clockwise positions, and the shorter ones the opposite.

The PWM signals of the Galileo Gen2 are generated by the chip PCA9685, which has 16 channels of PWM with a 12-bit-resolution, but just 6 are available in the Galileo's shield.
The frequency of the PWMs (all of them use the same one) may be programmed in a range from 24 Hz to 1525 Hz.

The PWMs can be accessed from the user's workspace in `/sys/class/pwm/pwmchip0`, where the following pseudo-files may be found:
-  npwm.
-  export.
-  unexport.
-  device/pwm_period.

The channels are numbered from 0 to npwm-1.

When a PWM channel *X* is exported, the following files are created in `/sys/class/pwm/pwmchip0/pwmX`:
-  period.
-  duty_cycle.
-  polarity (It can be changed just when the PWM is deactivated).

## Experiments

### Add a pwm group and configure init script in the root
```
$ groupadd -r pwm
$ groupmems -g pwm -a <USERNAME>
$ cp ~/eng10032lab06_1 /etc/init.d
$ chmod +x /etc/init.d/eng10032lab06_1
$ update-rc.d eng10032lab06_1 defaults
$ reboot
```

#### Fadding
```
$ ./fadding
```
[Watch it](https://photos.app.goo.gl/nGs9uTQNg8xFs4s69).

#### Servo
The voltage in the shield shall be changed to 5V first.
```
$ ./servo <ANGLE_DEGREES>
```
[Watch it](
https://photos.app.goo.gl/h7B2vzk4BKxTUd5y7).
