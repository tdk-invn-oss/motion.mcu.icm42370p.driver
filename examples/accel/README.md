# accel

This application demonstrates how to retrieve accel data. ODR is configured at 50 Hz.

## Command interface

This application allows the following command to be sent through UART:
* `s`: to toggle print data in SI unit (enabled/disabled, enabled by default).
* `l`: to toggle print data in LSB (enabled/disabled, disabled by default).
* `f`: to toggle FIFO usage (enabled/disabled, enabled by default). Data will be read from sensor registers if FIFO is disabled.
* `i`: to toggle FIFO highres mode usage (enabled/disabled, enabled by default). Only apply if FIFO is enabled.
* `p`: to toggle selected power-mode (low-noise/low-power, low-noise by default).
* `c`: to print current configuration.
* `h`: to print helps screen.

## Terminal output

### Data format

Data are printed on the terminal as follow:

* When print in SI unit is enabled:
```
SI <timestamp> us Accel: <acc_x> <acc_y> <acc_z> g Temp: <temp> degC FIFO time: <fifo_time> us
```
* When print in LSB is enabled:
```
LSB <timestamp> us Accel: <raw_acc_x> <raw_acc_y> <raw_acc_z> Temp: <raw_temp> FIFO time: <fifo_time> us
```

With:
* `timestamp`: Time in microsecond read from MCU clock when latest INT1 was fired
* `raw_acc_x|y|z`: Raw accel value
* `acc_x|y|z`: Accel value converted in g
* `raw_temp`: Raw temperature value
* `temp`: Temperature value converted in °C
* `fifo_time`: 16-bit timestamp field from FIFO.

### Example of output

```
[I] ###
[I] ### Example Accel
[I] ###
[I] SI        9209 us   Accel:       -        -        -     Temp:  23.50 degC   FIFO Time:  3232 us
[I] SI       29173 us   Accel:   -0.18    -0.80     0.50 g   Temp:  23.49 degC   FIFO Time: 23232 us
[I] SI       49139 us   Accel:   -0.19    -1.02     0.66 g   Temp:  23.46 degC   FIFO Time: 43232 us
[I] SI       69104 us   Accel:   -0.11    -0.99     0.74 g   Temp:  23.48 degC   FIFO Time: 63232 us
[I] SI       89069 us   Accel:   -0.14    -0.90     0.67 g   Temp:  23.45 degC   FIFO Time: 83232 us
[I] SI      109033 us   Accel:   -0.27    -0.86     0.59 g   Temp:  23.45 degC   FIFO Time: 103232 us
[I] SI      129000 us   Accel:   -0.18    -0.73     0.48 g   Temp:  23.46 degC   FIFO Time: 123232 us
[I] SI      148966 us   Accel:    0.11    -0.33     0.36 g   Temp:  23.48 degC   FIFO Time: 143232 us
[I] SI      168934 us   Accel:    0.13    -0.25     0.25 g   Temp:  23.45 degC   FIFO Time: 163232 us
[I] SI      188902 us   Accel:    0.08    -0.44     0.18 g   Temp:  23.48 degC   FIFO Time: 183232 us
[I] SI      208872 us   Accel:    0.02    -0.58    -0.18 g   Temp:  23.41 degC   FIFO Time: 203232 us
[I] SI      228839 us   Accel:    0.07    -0.78    -0.15 g   Temp:  23.44 degC   FIFO Time: 223232 us
[I] SI      248807 us   Accel:   -0.07    -0.89    -0.12 g   Temp:  23.47 degC   FIFO Time: 243232 us
[I] SI      268774 us   Accel:    0.10    -1.49     0.03 g   Temp:  23.43 degC   FIFO Time: 263232 us
[I] SI      288740 us   Accel:    0.35    -1.84     0.24 g   Temp:  23.45 degC   FIFO Time: 283232 us
[I] SI      308704 us   Accel:   -0.38    -1.64    -0.04 g   Temp:  23.49 degC   FIFO Time: 303232 us
[I] SI      328671 us   Accel:   -0.14    -1.60    -0.15 g   Temp:  23.49 degC   FIFO Time: 323232 us
[I] SI      348640 us   Accel:   -0.06    -1.51    -0.17 g   Temp:  23.49 degC   FIFO Time: 343232 us
[I] SI      368605 us   Accel:    0.03    -1.36    -0.27 g   Temp:  23.48 degC   FIFO Time: 363232 us
[I] SI      388570 us   Accel:   -0.08    -1.28    -0.26 g   Temp:  23.46 degC   FIFO Time: 383232 us
[I] SI      408536 us   Accel:    0.13    -1.53    -0.11 g   Temp:  23.41 degC   FIFO Time: 403232 us
[I] SI      428501 us   Accel:    0.10    -1.25    -0.03 g   Temp:  23.49 degC   FIFO Time: 423232 us
[I] SI      448470 us   Accel:   -0.01    -1.11    -0.04 g   Temp:  23.38 degC   FIFO Time: 443232 us
```

