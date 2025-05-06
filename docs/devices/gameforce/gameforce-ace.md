---
search:
  exclude: true
---

# GameForce Ace (WIP)

![](../../_inc/images/devices/gameforce-ace.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Interface |
| -- | -- | -- | -- | -- |
| Gameforce Ace | Rockchip RK3588 | Rockchip 5.10 BSP Linux | Panfrost | Weston + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |

## Controls

{%set btn_north = 'X(NORTH)' %}
{%set btn_west = 'Y(WEST)' %}
{%set btn_south = 'B(SOUTH)' %}
{%set btn_east = 'A(EAST)' %}
{%set btn_hotkey_a = 'Function' %}

{%include 'controls/retroarch.md' %}
{%include 'controls/mednafen.md' %}
{%include 'controls/mupen64plus.md' %}
{%include 'controls/ppsspp.md' %}
{%include 'controls/duckstation.md' %}
{%include 'controls/extra.md' %}

## Additional References

- [Platform Documentation (RK3588)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/RK3588)
