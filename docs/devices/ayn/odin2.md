---
search:
  exclude: true
---

# Ayn Odin 2

![](../../_inc/images/devices/ayn-odin-2.png){ .off-glb }

## Overview

| Device                        | CPU / Architecture      | Kernel         | GL driver | Vulkan driver | Interface                |
| ----------------------------- | ----------------------- | -------------- | --------- | ------------- | ------------------------ |
| Ayn Odin 2 (Base / Pro / Max) | Qualcomm 8gen2 (SM8550) | Mainline Linux | Freedreno | Turnip        | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes                                                                                                   |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| :material-wifi: Wifi                                                                                    | Can be turned on in Emulation Station under Main Menu > Network Settings                                |
| :simple-bluetooth: Bluetooth                                                                            | Supports bluetooth audio and controllers                                                                |
| :material-fan: Fan                                                                                      | Can be set globally, per system or per game.                                                            |
| :material-lightbulb-on: Joystick LEDS                                                                   | Supports selecting from a set of colors, battery level status, <br> or turning the joystick LEDS off.   |
| :material-vibrate: Rumble                                                                               | Can be turned on or off in Emulation Station under <br> Controller & Bluetooth Settings > Enable Rumble |

## Ayn Boot Selection for Linux

**Requires Ayn Odin 2 Firmware `v1.0.0.355` or newer** which adds support for Linux boot selection.

1. Power off the Odin 2 and insert your SD Card with ROCKNIX flashed on it
2. While holding down the VOL- button, press the power button and hold both buttons until you see the Ayn Log
3. The device should show the FastBoot Menu
4. Use the volume button to navigate the menu and change the `BOOT MODE` to `Loader`
5. Press power key to select `START`
6. Device will then boot into ROCKNIX off the SD Card

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
{%include 'controls/lime3ds.md' %}
{%include 'controls/azahar.md' %}

## Additional References

- [Platform Documentation (SM8550)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/SM8550)
