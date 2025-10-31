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
| :material-fan: Fan | Can be set globally, per system or per game. |
| :material-lightbulb-on: Joystick LEDS | Supports selecting from a set of colors, battery level status, <br>  or turning the joystick LEDS off. |

## Flashing LinuxLoader ABL

- [You must flash the Linux Loader ABL before you can boot ROCKNIX on the Odin 2.](https://renegade-project.tech/en/ayn-odin2/linuxloader) 
- [Alternative mirror: Extract the odin2_custom_abl folder to the root of Android internal storage. Then use Odin settings -> Run script as Root to run the backup_and_flash.sh script.](https://github.com/ROCKNIX/packages/raw/refs/heads/main/odin2_custom_abl_20250311.7z)

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
