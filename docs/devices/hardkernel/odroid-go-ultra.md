# Odroid Go Ultra

![](../../_inc/images/devices/hardkernel-odroid-go-ultra.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Interface |
| -- | -- | -- | -- | -- |
| Odroid Go Ultra | Amlogic S922X / Mali G52 M6 (ARMv8-A) | Mainline Linux | Mali | Weston + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-harddisk: Storage | ROCKNIX should be installed directly to the internal eMMC. <br> A microSD Card can be used for game storage. |

## :material-controller: Controls

{%set btn_north = 'X(NORTH)' %}
{%set btn_west = 'Y(WEST)' %}
{%set btn_south = 'B(SOUTH)' %}
{%set btn_east = 'A(EAST)' %}
{%include 'controls/retroarch.md' %}
{%set btn_hotkey_a = 'F1' %}
{%include 'controls/aethersx2.md' %}
{%set btn_menu = 'F1' %}
{%set btn_save = 'R2' %}
{%set btn_load = 'L2' %}
{%set btn_swap_a = 'L3' %}
{%set btn_swap_b = 'F2' %}
{%include 'controls/drastic.md' %}
{%include 'controls/dolphin.md' %}
{%include 'controls/lime3ds.md' %}
{%include 'controls/mupen64plus.md' %}
{%include 'controls/ppsspp.md' %}
{%include 'controls/yabasanshiro.md' %}
{%include 'controls/hypseus-singe.md' %}
{%include 'controls/openbor.md' %}
{%include 'controls/vice.md' %}
{%set btn_hotkey_b = 'Start' %}
{%include 'controls/extra.md' %}

## Notes

### Installation

First download the latest `S922X` version of ROCKNIX from the button below.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

To install ROCKNIX to the eMMC, you need to boot the device into recovery mode. There are 2 ways to do this:

1. Hardkernel Recovery SD
    - Download [this recovery image](https://wiki.odroid.com/odroid_go_ultra/os_image/recovery).
    - Follow the recovery steps on [the Odroid wiki](https://wiki.odroid.com/odroid_go_ultra/getting_started/recovery_eMMC).

2. ROCKNIX Recovery
    - hold ++"Volume Down"++ while the device boots.  

Once booted into recovery mode and connected to a PC via USB-C, the ROCKNIX image may be flashed to the eMMC using Balena Etcher, win32diskimager, dd or similar.

Once the ROCKNIX image has been flashed to the the eMMC, restart the device and ROCKNIX will go through its first boot process (running from eMMC).

## Additional References

- [Platform Documentation (S922X)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/S922X)
- [Odroid Go Ultra wiki](https://wiki.odroid.com/odroid_go_ultra/odroid_go_ultra)
