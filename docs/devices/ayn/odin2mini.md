---
search:
  exclude: true
---

# Ayn Odin 2 Mini

![](../../_inc/images/devices/ayn-odin-2-mini.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Vulkan driver | Interface |
| -- | -- | -- | -- | -- | -- |
| Ayn Odin 2 Mini | Qualcomm 8gen2 (SM8550) | Mainline Linux | Freedreno | Turnip | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-fan: Fan | Managed by the kernel. |
| :material-lightbulb-on: Joystick LEDS | Supports selecting from a set of colors, battery level status, <br>  or turning the joystick LEDS off. |
| :material-sleep: Suspend | See: [Fake Suspend](../../../configure/fake-suspend) |

## Flashing ROCKNIX ABL

- These steps are only required if your device doesn't have a fastboot menu to switch the Boot Mode.
- In Android, copy the folder `rocknix_abl` from the SD card to the root of the Internal Storage.
- Execute as root the scipt `backup_abl.sh`, then `flash_abl.sh`
- Reboot device holding Vol - key to enter fastboot menu.
- Use Vol -/+ to change the option to "Switch boot mode"
- Hit Power Button to validate.
- Hit Power Button again to start ROCKNIX.

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
