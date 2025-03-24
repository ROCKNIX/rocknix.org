# Powkiddy RGB10 Max 3 Pro

![](../../_inc/images/devices/powkiddy-rgb10max3pro.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Interface |
| -- | -- | -- | -- | -- |
| RGB10 Max 3 Pro | Amlogic A311D / Mali G52 M4 (ARMv8-A) | Mainline Linux | Mali | Weston + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-harddisk: Storage | ROCKNIX should be installed directly to the internal eMMC. <br> When installed directly to the eMMC; an SD Card can be used for game storage. |

## Controls

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

Download the latest `S922X` version of ROCKNIX from the button below.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

To install ROCKNIX to the eMMC, you need to boot the device into recovery mode. There are 2 ways to do this:

1. Hardkernel Recovery SD
    - Download [this recovery image](https://wiki.odroid.com/odroid_go_ultra/os_image/recovery).
    - Flash the image to a spare microSD card using Balena Etcher or similar.
    - Remove the back cover of the device (four screws).
    - Locate a small button on the back of the board (the side that's visible), near the right thumbstick.
    - While holding down the small button, power on the device.

The device should now be in recovery mode, ready to flash ROCKNIX (or other firmware) to the device.

If you find yourself doing this often, consider drilling a pinhole in the back cover so that the button can be accessed with a paperclip.

![](../../_inc/images/devices/mods/powkiddy-rgb10max3pro-mod1.png){ .off-glb }

2. ROCKNIX Recovery
    - hold ++"Volume Down"++ while the device boots.  

Once booted into recovery mode and connected to a PC via USB-C, the ROCKNIX image may be flashed to the eMMC using Balena Etcher, win32diskimager, dd or similar.

Once the ROCKNIX image has been flashed to the the eMMC, restart the device and ROCKNIX will go through its first boot process (running from eMMC).

## Additional References

- [Platform Documentation (S922X)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/S922X)
- [Odroid Go Ultra wiki](https://wiki.odroid.com/odroid_go_ultra/odroid_go_ultra)

### Community Videos

| <iframe width="560" height="315" src="https://www.youtube.com/embed/X9wbPY5qf6o?si=nIUFXmEcsRswl2ij&amp;start=316" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> | <iframe width="560" height="315" src="https://www.youtube.com/embed/_dXk5UjZ_Kg?si=AxdJyrBZ4JamiHqq&amp;start=316" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> |
| -- | -- |
| <iframe width="560" height="315" src="https://www.youtube.com/embed/3y8RJ33CQ2A?si=y4vckUqDAsfP362J&amp;start=316" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> |



