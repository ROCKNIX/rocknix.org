# Odroid Go Advance

![](../../_inc/images/devices/hardkernel-odroid-go-advance.png){ .off-glb }

## Overview
{%set hw_display = '3.5-inch 480*320' %}
{%set hw_emmc = 'None' %}
{%set hw_connectivity = 'Black Edition: 2.4 GHz (ESP32-S2)' %}
{%set hw_ram = '1 GB DDR3L' %}
{% include "platforms/rk3326.md" %}

## Notes

### Installation

Download the latest `RK3326` version of ROCKNIX from the button below and follow the instructions listed on the [Install](../../../play/install/) page.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

### Analogue Stick

There are several parameters available for the analogue stick in the [odroidgo2_joypad driver](https://github.com/hardkernel/linux/blob/73c2cbdb49d240c408bd16a717215c1d4bed529f/drivers/input/joystick/odroidgo2-joypad.c). These can be used to work around stick drift, or a disconnected stick, perhaps due to a broken connector on the mainboard (which causes stick input to the right to permanently register).

| Parameter | Notes |
| -- | -- |
| joystick_fuzz | 0 - 1800, used to filter noise from the event stream |
| joystick_flat | 0 - 1800 |
| joystick_y_range | 0 - 1800 |
| joystick_x_range | 0 - 1800 |
| joystick_scale | |
| joystick_deadzone | 0 - 1800 |

To override a parameter value, modify bootargs in boot.ini. For example to disable the analogue stick input, modify boot.ini to use the following values as per this [Odroid forum post](https://forum.odroid.com/viewtopic.php?p=307850&sid=99d227d2c69e6eb1d67dc10ac44d969b#p307850):
```
setenv joystick_fuzz "1800"
setenv joystick_flat "1800"
setenv joystick_y_range "1800"
setenv joystick_x_range "1800"
setenv joystick_scale "2"
setenv joystick_deadzone "1800"
setenv joystick_config "button-adc-x-range=${joystick_x_range} button-adc-y-range=${joystick_y_range} button-adc-fuzz=${joystick_fuzz} button-adc-flat=${joystick_flat} button-adc-scale=${joystick_scale} button-adc-deadzone=${joystick_deadzone}"

setenv bootargs "<snip - existing bootargs> ${joystick_config}"
```

## Additional References

- [Platform Documentation (RK3326)](https://github.com/ROCKNIX/distribution/tree/next/documentation/PER_DEVICE_DOCUMENTATION/RK3326)
