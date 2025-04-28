# Powkiddy RGB20SX

![](../../_inc/images/devices/powkiddy-rgb20sx.png){ .off-glb }

## Overview
{%set hw_display = '4-inch 720*720' %}
{%set hw_emmc = 'None' %}
{%set hw_connectivity = '2.4 GHz WiFi + BT (RTL8723DS)' %}
{%set hw_ram = '1 GB LPDDR4' %}
{% include "platforms/rk3566.md" %}

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-harddisk: Storage | ROCKNIX can be run from an SD Card and an second SD card can be used to store games |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |

## Controls

{%set btn_north = 'X(NORTH)' %}
{%set btn_west = 'Y(WEST)' %}
{%set btn_south = 'B(SOUTH)' %}
{%set btn_east = 'A(EAST)' %}

{%include 'controls/retroarch.md' %}
{%include 'controls/mednafen.md' %}
{%include 'controls/mupen64plus.md' %}
{%include 'controls/ppsspp.md' %}
{%include 'controls/hypseus-singe.md' %}
{%include 'controls/duckstation.md' %}
{%include 'controls/extra.md' %}

## Emulators

- [Platform Documentation (RK3566)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/RK3566)

## Notes

### Installation

Download the latest `RK3566` version of ROCKNIX from the button below and follow the instructions listed on the [Install](../../../play/install/) page.  Insert the SD card into the TF-OS slot of the device and power it on.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)
