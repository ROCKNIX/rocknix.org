---
search:
  exclude: true
---

# Mangmi Air X

![](../../_inc/images/devices/mangmi-air-x.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Vulkan driver | Interface |
| -- | -- | -- | -- | -- | -- |
| Retroid Pocket 5 | Qualcomm SD662 (SM6115) | Mainline Linux | Freedreno | Turnip | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-lightbulb-on: Joystick LEDS | Supports selecting from a set of colors, battery level status, <br>  or turning the joystick LEDS off. |
| :material-vibrate: Rumble | Can be turned on or off in Emulation Station under <br> Controller & Bluetooth Settings > Enable Rumble |

## Controls

{%set btn_north = 'X(NORTH)' %}
{%set btn_west = 'Y(WEST)' %}
{%set btn_south = 'B(SOUTH)' %}
{%set btn_east = 'A(EAST)' %}
{%set btn_hotkey_a = 'HOME' %}

{%include 'controls/extra.md' %}
{%include 'controls/aethersx2.md' %}
{%include 'controls/azahar.md' %}
{%include 'controls/drastic.md' %}
{%include 'controls/dolphin.md' %}
{%include 'controls/duckstation.md' %}
{%include 'controls/hypseus-singe.md' %}
{%include 'controls/melonds.md' %}
{%include 'controls/mupen64plus.md' %}
{%include 'controls/openbor.md' %}
{%include 'controls/ppsspp.md' %}
{%include 'controls/retroarch.md' %}
{%include 'controls/vice.md' %}
{%include 'controls/yabasanshiro.md' %}

## Installation

### Step 1: Image SD card

First download the latest `SM6115` version of ROCKNIX from the button below  and follow the instructions listed on the [Install](../../../play/install/) page.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution-nightly/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution-nightly/releases/latest)

### Step 2: Install ROCKNIX Android Bootloader (ABL)

Once you have written the image to an SD card, insert the card and boot into Android.

Navigate to Settings -> Handheld Settings -> Advanced -> Run Script as Root.

Select the `rocknix-abl` folder on the `ROCKNIX` SD card. Select the `backup_abl.sh` script to flash the ROCKNIX ABL. Select the `flash_abl.sh` script to flash the ROCKNIX ABL.

!!! note "If GammaOS is installed rather than stock Android, run the `backup_abl.sh` and `flash_abl.sh` scripts in an Android Debug Bridge (adb) shell."

### Step 3: Configure ROCKNIX ABL

Restart your device, holding Vol- as it boots to enter the ROCKNIX ABL. Within the ROCKNIX ABL, use Vol- / Vol+ to navigate between options and Power to select.

Navigate to 'Set device model' and select MQ65 / MQ66 as appropriate.

Navigate to 'Switch boot mode' and switch it to 'Linux'. Navigate to 'Start' to boot into ROCKNIX.

## Additional References

- [Platform Documentation (SM6115)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/SM6115)
