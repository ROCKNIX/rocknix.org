# Powkiddy RGB10 Max 3 Pro

![](../../_inc/images/devices/powkiddy-rgb10max3pro.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Interface |
| -- | -- | -- | -- | -- |
| RGB10 Max 3 Pro | Amlogic A311D / Mali G52 M4 (ARMv8-A) | Mainline Linux | Mali | Weston + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-harddisk: Storage | ROCKNIX should be installed directly to the internal EMMC. <br> When installed directly to the EMMC; an SD Card can be used for game storage. |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |

## Controls

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

## Emulators

- [Platform Documentation (S922X)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/S922X)

## Notes

### Installation

Download the latest `S922X-Odroid_GOU` version of ROCKNIX from the button below.

!!! note "ROCKNIX must be flashed directly onto the RGB10 Max 3 Pro rather than an SD card.  This is done by putting the device into recovery mode, per the manual by holding down R2, L2, and power. A video demonstation [is shown here](https://youtu.be/X9wbPY5qf6o?t=1195)."

[![Latest Version](https://img.shields.io/github/release/JustEnoughLinuxOS/distribution.svg?labelColor=111111&color=5998FF&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/JustEnoughLinuxOS/distribution.svg?labelColor=dddddd&color=5998FF&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

### Troubleshooting

You cannot brick this device. If you cannot get into recovery mode, do the following:

- Download [this recovery image](https://wiki.odroid.com/odroid_go_ultra/os_image/recovery).
- Flash the image to a spare microSD card using Balena Etcher or similar.
- Remove the back cover of the device (four screws).
- Locate a small button on the back of the board (the side that's visible), near the right thumbstick.
- While holding down the small button, power on the device.

The device should now be in recovery mode, ready to flash ROCKNIX (or other firmware) to the device.

If you find yourself doing this often, consider drilling a pinhole in the back cover so that the button can be accessed with a paperclip.

![](../../_inc/images/devices/mods/powkiddy-rgb10max3pro-mod1.png){ .off-glb }

### Community Videos

| <iframe width="560" height="315" src="https://www.youtube.com/embed/X9wbPY5qf6o?si=nIUFXmEcsRswl2ij&amp;start=316" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> | <iframe width="560" height="315" src="https://www.youtube.com/embed/_dXk5UjZ_Kg?si=AxdJyrBZ4JamiHqq&amp;start=316" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> |
| -- | -- |
| <iframe width="560" height="315" src="https://www.youtube.com/embed/3y8RJ33CQ2A?si=y4vckUqDAsfP362J&amp;start=316" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> |



