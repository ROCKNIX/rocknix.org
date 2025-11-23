---
search:
  exclude: true
---

# AYANEO Pocket EVO (SM8550)

![](../../_inc/images/devices/ayaneo-pocket-evo.png){ .off-glb }

## Overview

| Device                        | CPU / Architecture      | Kernel         | GL driver | Vulkan driver | Interface                |
| ----------------------------- | ----------------------- | -------------- | --------- | ------------- | ------------------------ |
| AYANEO Pocket EVO | Qualcomm G3x Gen2 (SM8550) | Mainline Linux | Freedreno | Turnip        | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes                                                                                                   |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| :material-wifi: Wifi                                                                                    | Can be turned on in Emulation Station under Main Menu > Network Settings                                |
| :simple-bluetooth: Bluetooth                                                                            | Supports bluetooth audio and controllers                                                                |
| :material-fan: Fan | Managed by the kernel. |
| :material-lightbulb-on: Joystick LEDS                                                                   | Supports selecting from a set of colors, battery level status, <br> or turning the joystick LEDS off.   |
| :material-vibrate: Rumble                                                                               | Can be turned on or off in Emulation Station under <br> Controller & Bluetooth Settings > Enable Rumble |

## Flashing LinuxLoader ABL

- In Android, copy the folder `rocknix_abl` from the SD card to the root of the Internal Storage.
- Execute as root the scipt `backup_abl.sh`, then `flash_abl.sh`
- Copy the file on the SD card `/device_trees/u-boot-pocket-evo.dtb` in the root of the SD card.
- Rename the file `/u-boot-pocket-evo.dtb` as `/dtb.img`

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

## Additional References

- [Platform Documentation (SM8550)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/SM8550)
