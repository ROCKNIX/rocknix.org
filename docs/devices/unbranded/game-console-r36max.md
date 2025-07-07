# Game Console R36Max/R36Pro/K36

## Work in progress
Use [Custom build](https://github.com/stolen/r.nix-distribution/releases/tag/k36-emmc-wip) and do not upgrade while this notice is here.

![](../../_inc/images/devices/unbranded-game-console-r36max.png){ .off-glb }

## Overview
{%set hw_display = '4.0-inch 720*720' %}
{%set hw_emmc = '8 GB' %}
{%set hw_connectivity = 'None' %}
{%set hw_ram = '1 GB DDR3' %}
{% include "platforms/rk3326.md" %}

## Controls

{%set btn_north = 'Y(NORTH)' %}
{%set btn_west = 'X(WEST)' %}
{%set btn_south = 'A(SOUTH)' %}
{%set btn_east = 'B(EAST)' %}

{%include 'controls/retroarch.md' %}
{%include 'controls/mednafen.md' %}
{%include 'controls/extra.md' %}

## Emulators

- [Platform Documentation (RK3326)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/RK3326)

## Notes

### Installation

This family has WiP status. Release kinda works, but needs manual intervention.  
Use the image and instructions from [Custom build](https://github.com/stolen/r.nix-distribution/releases/tag/k36-emmc-wip). Basic flashing instructions are on the [Install](../../../play/install/) page.
