---
search:
  exclude: true
---

# Ayn Odin 2 Portal

![](../../_inc/images/devices/ayn-odin-2-portal.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Vulkan driver | Interface |
| -- | -- | -- | -- | -- | -- |
| Ayn Odin 2 Portal | Qualcomm 8gen2 (SM8550) | Mainline Linux | Freedreno | Turnip | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-fan: Fan | Managed by the kernel. |
| :material-lightbulb-on: Joystick LEDS | Supports selecting from a set of colors, battery level status, <br>  or turning the joystick LEDS off. |

## Ayn Boot Selection for Linux

1. Power off the Odin 2 Portal and insert your SD Card with ROCKNIX flashed on it
2. While holding down the VOL- button, press the power button and hold both buttons until you see the Ayn Log
3. The device should show the FastBoot Menu
4. Use the volume button to navigate the menu and change the `BOOT MODE` to `Loader`
5. Press power key to select `START`
6. Device will then boot into ROCKNIX off the SD Card

## Flashing LinuxLoader ABL

- These steps are only required if your device doesn't have a fastboot menu to switch the Boot Mode.
- In Android, copy the folder `rocknix_abl` from the SD card to the root of the Internal Storage.
- Execute as root the scipt `backup_abl.sh`, then `flash_abl.sh`
- Copy the file on the SD card `/device_trees/u-boot-odin2.dtb` in the root of the SD card.
- Rename the file `/u-boot-odin2.dtb` as `/dtb.img`

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
{%include 'controls/azahar.md' %}

## Additional References

- [Platform Documentation (SM8550)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/SM8550)
