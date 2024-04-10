# Odroid Go Ultra

![](../../_inc/images/devices/hardkernel-odroid-go-ultra.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Interface |
| -- | -- | -- | -- | -- |
| Odroid Go Ultra | Amlogic S922X / Mali G52 M6 (ARMv8-A) | Mainline Linux | Mali | Weston + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-harddisk: Storage | ROCKNIX should be installed directly to the internal EMMC. <br> A microSD Card can be used for game storage. |

## :material-controller: Controls

{%set btn_north = 'X(NORTH)' %}
{%set btn_west = 'Y(WEST)' %}
{%set btn_south = 'B(SOUTH)' %}
{%set btn_east = 'A(EAST)' %}
{%include 'controls/retroarch.md' %}
{%set btn_prefix = 'F1' %}
{%include 'controls/aethersx2.md' %}
{%include 'controls/lime3ds.md' %}
{%set btn_save = 'R2' %}
{%set btn_load = 'L2' %}
{%set btn_menu = 'F1' %}
{%set btn_swap_a = 'L3' %}
{%set btn_swap_b = 'F2' %}
{%include 'controls/drastic.md' %}
{%include 'controls/dolphin.md' %}
{%include 'controls/mupen64plus.md' %}
{%include 'controls/ppsspp.md' %}
{%include 'controls/yabasanshiro.md' %}
{%include 'controls/hypseus-singe.md' %}
{%include 'controls/openbor.md' %}
{%include 'controls/vice.md' %}
{%set btn_pre1 = 'F1' %}
{%set btn_pre2 = 'F2' %}
{%include 'controls/extra.md' %}

## Notes

### Installation

First download the latest `S922X-Odroid_GOU` version of ROCKNIX from the button below.

[![Latest Version](https://img.shields.io/github/release/JustEnoughLinuxOS/distribution.svg?labelColor=111111&color=5998FF&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/JustEnoughLinuxOS/distribution.svg?labelColor=dddddd&color=5998FF&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

Installation process:

1. Boot the Odroid Go Ultra into recovery mode following the steps on [the Odroid wiki](https://wiki.odroid.com/odroid_go_ultra/getting_started/installing_os_image#installation).
2. Once booted into recovery mode and connected to a PC via USB-C, the ROCKNIX image may be flashed to the EMMC using Balena Etcher, win32diskimager, dd or similar.
3. Restart the device and ROCKNIX will go through its first boot process (running from EMMC).

### Troubleshooting

You cannot brick this device. If you cannot get into recovery mode, do the following:

- Download [this recovery image](https://wiki.odroid.com/odroid_go_ultra/os_image/recovery).
- Follow the recovery steps on [the Odroid wiki](https://wiki.odroid.com/odroid_go_ultra/getting_started/recovery_emmc)

The device should now be in recovery mode, ready to flash ROCKNIX (or other firmware) to the device.

## Additional References

- [Platform Documentation (S922X)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/S922X)
- [Odroid Go Ultra wiki](https://wiki.odroid.com/odroid_go_ultra/odroid_go_ultra)
