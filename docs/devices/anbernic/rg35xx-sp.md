# Anbernic RG35XX SP

![](../../_inc/images/devices/anbernic-rg35xxsp.png){ .off-glb }

## Overview
{%set hw_display = '3.5-inch 640*480' %}
{%set hw_emmc = 'None' %}
{%set hw_connectivity = '2.4/5 GHz WiFi + BT' %}
{%set hw_ram = '1 GB LPDDR4' %}
{% include "platforms/h700.md" %}

| Device | CPU / Architecture | Kernel | GL driver | Interface |
| -- | -- | -- | -- | -- |
| RG35XX SP | Allwinner H700 (ARM) | Mainline Linux | Panfrost | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-harddisk: Storage | ROCKNIX can be run from an SD Card and an second SD card can be used to store games |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-lightbulb-on: LED | Supports selecting from a set of colors or turning the power LED off (choice persists through reboots) <br> Does not support other effects. |

## Controls

{%set btn_north = 'X(NORTH)' %}
{%set btn_west = 'Y(WEST)' %}
{%set btn_south = 'B(SOUTH)' %}
{%set btn_east = 'A(EAST)' %}
{%set btn_hotkey_a = 'MENU' %}

{%include 'controls/retroarch.md' %}
{%include 'controls/mednafen.md' %}
{%include 'controls/mupen64plus.md' %}
{%include 'controls/ppsspp.md' %}
{%include 'controls/hypseus-singe.md' %}
{%include 'controls/extra.md' %}

## Notes

### Installation

!!! note "The H700 release of ROCKNIX is not yet available."

Download the latest `H700` version of ROCKNIX from the button below and follow the instructions listed on the [Install](../../../play/install/) page.

Important, before booting the device, edit the file `extlinux/extlinux.conf` and change the line `  FDT /sun50i-h700-anbernic-rg35xx-plus` to `  FDT /sun50i-h700-anbernic-rg35xx-sp.dtb`.

If the display doesn't seems to works (flickering, noise, etc...), you may have a version with a new display, in that case use `  FDT /sun50i-h700-anbernic-rg35xx-sp-rev6-panel.dtb`

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

## Additional References

- [Platform Documentation (H700)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/H700)
