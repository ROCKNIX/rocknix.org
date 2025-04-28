# Powkiddy RGB10X

![](../../_inc/images/devices/powkiddy-rgb10x.png){ .off-glb }

## Overview
{%set hw_display = '3.5-inch 640*480' %}
{%set hw_emmc = 'None' %}
{%set hw_connectivity = 'None' %}
{%set hw_ram = '1 GB DDR3L' %}
{% include "platforms/rk3326.md" %}

## Controls

{%set btn_north = 'Y(NORTH)' %}
{%set btn_west = 'X(WEST)' %}
{%set btn_south = 'A(SOUTH)' %}
{%set btn_east = 'B(EAST)' %}

{%include 'controls/retroarch.md' %}

{% set btn_hotkey_a = '-(MINUS)' %}
{% set btn_hotkey_b = '\+(PLUS)' %}
{%include 'controls/mednafen.md' %}
{%include 'controls/duckstation.md' %}

## Emulators

- [Platform Documentation (RK3326)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/RK3326)

## Notes

### Installation

Download the latest `RK3326` version of ROCKNIX from the button below and follow the instructions listed on the [Install](../../../play/install/) page.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)
