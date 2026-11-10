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
| :material-progress-check: Internal installation | See: [installtointernal](../../../play/installtointernal) |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-fan: Fan | Managed by the kernel. |
| :material-lightbulb-on: Joystick LEDS | Supports selecting from a set of colors, battery level status, <br>  or turning the joystick LEDS off. |
| :material-sleep: Suspend | See: [Fake Suspend](../../../configure/fake-suspend) |

## Flashing OpenABL

{%include 'openabl/install.md' %}
{%include 'openabl/configure.md' %}

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
{%include 'controls/gopher64.md' %}
{%include 'controls/bigpemu.md' %}

## Additional References

- [Platform Documentation (SM8550)](https://github.com/ROCKNIX/distribution/tree/next/documentation/PER_DEVICE_DOCUMENTATION/SM8550)
