# Game Console R35S/R36S

![](../../_inc/images/devices/unbranded-game-console-r36s.png){ .off-glb }

## Overview
{%set hw_display = '3.5-inch 640*480' %}
{%set hw_emmc = 'None' %}
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
{%include 'controls/duckstation.md' %}
{%include 'controls/extra.md' %}

## Emulators

- [Platform Documentation (RK3326)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/RK3326)

## Notes

### Installation

Download the latest `RK3326` version of ROCKNIX from the button below and follow the instructions listed on the [Install](../../../play/install/) page.

[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)
[![Latest Version](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

### New displays (R36s of year 2024)

Recent R36s have new displays that need some extra actions to work.

The simplest way so far is:

* Determine which panel do you have (or just try every option until it works)
* Download a `mipi-panel.dtbo.r36s-panel*` [there](https://github.com/stolen/r.nix-distribution/releases/tag/panel_overlays)
* Rename the downloaded file and put it to a boot (`ROCKNIX`) partition as `overlays/mipi-panel.dtbo`

These files mostly have just basic refresh rate (77.378 FPS) (`panel4` has 50, 60, 75 because we tested it)

If you have an original `.dtb` file, you can generate a `mipi-panel.dtbo` from it.  
Assuming you have an [SSH](/faqs/#how-do-i-log-in-over-ssh-or-samba) access and you have `scp`'d the original dtb as `rk3326-r35s-linux.dtb`, the process would be as follows:
```console
RK3326:~ # mount -o remount,rw /flash
RK3326:~ # mkdir -p /flash/overlays/
RK3326:~ # ### Be not afraid! importpanel.py may run for a minute or two for some panels
RK3326:~ # /usr/libexec/generic-dsi/importpanel.py rk3326-r35s-linux.dtb -O dtbo -o /flash/overlays/mipi-panel.dtbo
RK3326:~ # sync; mount -o remount,ro /flash/
```
Here we just make an overlays directory writable, then call a script that does all the importing stuff.  
Feel free to run this script on your PC, modify it and experiment with panel timings.  

This script adds a bunch of potentially useful refresh rates, but we have very few knowledge on which modes work well.  
Please check them with `wlr-randr` or with game configuration and tell us which modes work with your panel.
