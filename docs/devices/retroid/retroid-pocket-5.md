---
search:
  exclude: true
---

# Retroid Pocket 5

![](../../_inc/images/devices/retroid-pocket-5.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Vulkan driver | Interface |
| -- | -- | -- | -- | -- | -- |
| Retroid Pocket 5 | Qualcomm SD865 (SM8250) | Mainline Linux | Freedreno | Turnip | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-fan: Fan | Can be set globally, per system or per game. |
| :material-lightbulb-on: Joystick LEDS | Supports selecting from a set of colors, battery level status, <br>  or turning the joystick LEDS off. |
| :material-vibrate: Rumble | Can be turned on or off in Emulation Station under <br> Controller & Bluetooth Settings > Enable Rumble |
| :material-monitor: Dual Screen Addon | Currently only supported through manual configuration. |

## Controls

{%set btn_north = 'X(NORTH)' %}
{%set btn_west = 'Y(WEST)' %}
{%set btn_south = 'B(SOUTH)' %}
{%set btn_east = 'A(EAST)' %}
{%set btn_hotkey_a = 'HOME' %}

{%include 'controls/extra.md' %}
{%include 'controls/retroarch.md' %}
{%include 'controls/mupen64plus.md' %}
{%include 'controls/ppsspp.md' %}
{%include 'controls/dolphinqt.md' %}
{%include 'controls/dolphin.md' %}
{%include 'controls/aethersx2.md' %}
{%include 'controls/xemu.md' %}
{%include 'controls/duckstation.md' %}
{%include 'controls/azahar.md' %}

## Dual Screen
These commands will configure the Dual Screen, you will need to login to your device using SSH to run them.

You will need to toggle the "Enable SSH" option by pressing ++"START"++ and going to ```Network Settings```. Also make sure that "Enable Wifi" is also toggled and your device is connected to your network. The IP address of your device can be found at the top of the ```Network Settings``` menu

To configure screen orientation and resolution
```bash
swaymsg output DP-1 transform 270
swaymsg output DP-1 bg #000000 solid_color
swaymsg output DP-1 allow_tearing yes
swaymsg output DP-1 max_render_time off
swaymsg output DP-1 scale 2
swaymsg output DP-1 position 0 0
systemctl restart essway.service
```

To mirror the dual screen on the main screen, run these commands in addition to the ones above
```bash
swaymsg output DSI-1 scale 2
swaymsg output DSI-1 position 0 0
systemctl restart essway.service
```

For the touch screen
```bash
swaymsg input "8746:1:RetroidPocket_RDS_Touchscreen" map_to_output "DP-1"
swaymsg input "8746:1:RetroidPocket_RDS_Touchscreen" calibration_matrix "0 1 0 -1 0 1"
```

However, this configuration is only temporary, as the settings will revert if the device is shutdown or restarted. 
Additonally, these commands can be placed into a script and ran from the file manager to bypass the need to ssh.

## Additional References

- [Platform Documentation (SM8250)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/SM8250)

### Community Videos

| <iframe width="560" height="315" src="https://www.youtube.com/embed/PtZKzzWysw8?si=Zg8OB4gFO9aRG0Hb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> |
