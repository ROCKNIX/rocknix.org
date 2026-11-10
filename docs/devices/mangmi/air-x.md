---
search:
  exclude: true
---

# Mangmi Air X

![](../../_inc/images/devices/mangmi-air-x.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Vulkan driver | Interface |
| -- | -- | -- | -- | -- | -- |
| Mangmi Air X | Qualcomm SD662 (SM6115) | Mainline Linux | Freedreno | Turnip | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-progress-check: Internal installation | See: [installtointernal](../../../play/installtointernal) |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-lightbulb-on: Joystick LEDS | Supports selecting from a set of colors, battery level status, <br>  or turning the joystick LEDS off. |
| :material-sleep: Suspend | See: [Fake Suspend](../../../configure/fake-suspend) |

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

First download the `SM6115` version of ROCKNIX from the [Latest Nightly Build](https://github.com/ROCKNIX/distribution-nightly/releases/latest) and follow the instructions listed on the [Install](../../../play/install/) page.

<!-- [![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution-nightly/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution-nightly/releases/latest) -->

### Step 2: Install OpenABL

{%set abl_scripts = 'run_script_as_root' %}
{%include 'openabl/install.md' %}

!!! note "If GammaOS is installed rather than stock Android, run the `backup_abl.sh` and `flash_abl.sh` scripts in an Android Debug Bridge (adb) shell."

### Step 3: Configure OpenABL

{%set abl_device = "MQ65 / MQ66 as appropriate" %}
{%include 'openabl/configure.md' %}

## Additional References

- [Platform Documentation (SM6115)](https://github.com/ROCKNIX/distribution/tree/next/documentation/PER_DEVICE_DOCUMENTATION/SM6115)
