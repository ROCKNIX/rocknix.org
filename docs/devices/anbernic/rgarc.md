# Anbernic RG ARC [D/S]

![](../../_inc/images/devices/anbernic-rgarc.png){ .off-glb }

## Overview
!!! warning "eMMC model with legacy bootloader is not supported."

{%set hw_display = '4-inch 640*480' %}
{%set hw_emmc = '32GB (D)' %}
{%set hw_connectivity = '2.4/5 GHz WiFi + BT' %}
{%set hw_ram = '1 GB (S), 2 GB (D) LPDDR4' %}
{% include "platforms/rk3566.md" %}

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-harddisk: Storage | ROCKNIX can be installed to the eMMC on the D model or run from an SD Card, and an second SD card can be used to store games |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |

## Controls

{%set btn_north = 'Y(NORTH)' %}
{%set btn_west = 'X(WEST)' %}
{%set btn_south = 'A(SOUTH)' %}
{%set btn_east = 'B(EAST)' %}

{%include 'controls/retroarch.md' %}
{%include 'controls/mednafen.md' %}

{%set btn_west = 'X' %}
{%set btn_south = 'A' %}
{%set btn_c_up = 'Z' %}
{%set btn_c_down = 'B' %}
{%set btn_c_left = 'Y' %}
{%set btn_c_right = 'C' %}
{%include 'controls/mupen64plus.md' %}

* The default mapping maps the Nintendo 64 joystick to the d-pad, by selecting custom input configuration in advanced game options it will map the Nintendo 64 d-pad to the Arc d-pad.

{%include 'controls/ppsspp.md' %}
{%include 'controls/hypseus-singe.md' %}
{%include 'controls/duckstation.md' %}
{%include 'controls/extra.md' %}

## Notes

### Installation

Download the latest `RK3566` version of ROCKNIX from the button below and follow the instructions listed on the [Install](../../../play/install/) page.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

##### RG-ARC-D Users

{%include 'platforms/android-wipe.md' %}

## Additional References

- [Platform Documentation (RK3566)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/RK3566)
