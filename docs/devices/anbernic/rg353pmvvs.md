# Anbernic RG353 [P/M/V/VS/PS]

![](../../_inc/images/devices/anbernic-rg353.png){ .off-glb }

## Overview
!!! warning "eMMC models with legacy bootloader is not supported."
!!! info "Anbernic RG353P/M/V/VS devices with both v1 and v2 displays are supported."

{%set hw_display = '3.5-inch 640*480' %}
{%set hw_emmc = '32GB (P/M/V)' %}
{%set hw_connectivity = '2.4/5 GHz WiFi + BT' %}
{%set hw_ram = '1 GB (VS/PS), 2 GB (P/M/V) LPDDR4' %}
{% include "platforms/rk3566.md" %}


## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-harddisk: Storage | ROCKNIX can be installed to the emmc on P/M/V models or run from an SD Card, and an second SD card can be used to store games |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-lightbulb-on: LED | Supports selecting from a set of colors or turning the power LED off (choice persists through reboots) <br> Does not support other effects. |

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

## Notes

### Installation

Download the latest `RK3566` version of ROCKNIX from the button below and follow the instructions listed on the [Install](../../../play/install/) page.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

##### P/M/V Users

{%include 'platforms/android-wipe.md' %}

## Additional References

- [Platform Documentation (RK3566)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/RK3566)
- [Device Quirks (353P/M)](https://github.com/ROCKNIX/distribution/tree/main/packages/hardware/quirks/devices/Anbernic%20RG353P)
- [Device Quirks (353V)](https://github.com/ROCKNIX/distribution/tree/main/packages/hardware/quirks/devices/Anbernic%20RG353V)

## Community Videos

| <iframe width="560" height="315" src="https://www.youtube.com/embed/tJR0Evx3KS0?si=UNCRp6nQWJClLo0H" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> | <iframe width="560" height="315" src="https://www.youtube.com/embed/MjyyxyIcEto?si=wYlVT6oRjsCGg0Hh" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> |
| -- | -- |
| <iframe width="560" height="315" src="https://www.youtube.com/embed/Q9zETew3iuY?si=PiOlyviTPN3QDQqb&amp;start=1104" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> | <iframe width="560" height="315" src="https://www.youtube.com/embed/vnHRKn9FoVw?si=OuJyNbTn3rdJNvNa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> |
