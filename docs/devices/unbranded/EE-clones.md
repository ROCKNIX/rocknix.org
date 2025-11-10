# Game Console K36, R36Max/Pro, MyMini, xf35h/xf40h and other "EE clones"

!!! info "These devices have experimental support"

    Make sure you use nightly `20251110` or newer, older builds are more broken

## About the family
These are mostly similar but subtely different devices. K36 was likely the first one, thus "K36 family".  
Some of the devices mimicked "classic" R36s pretty well, thus "clones".  
Seem to be designed by a single team, run the same software:  

- EmuElec by default thus "EE clones"
- `play_joystick` input driver (patched and renamed variant of something else)

To deal with the variety, hardware configuration is partially imported from stock `dtb` file.
This doesn't yield to a perfect result and sometimes needs extra tweaks, but usually works.  

![](../../_inc/images/devices/unbranded-game-console-r36max.png){ .off-glb }

## Overview

{%set hw_display = '4.0-inch 720x720, 3.5-inch 640x480 and others' %}
{%set hw_emmc = '8 GB (often)' %}
{%set hw_connectivity = 'rk915 2.4G WiFi (sometimes)' %}
{%set hw_ram = 'usually 1 GB DDR3, sometimes 512M' %}

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

1. Flash `B` image to SD
2. If your device has a stock firmware on SD, move that card to SD2 (GAME) slot
3. Insert Rocknix SD to SD1 (OS) slot (or the only slot for some devices with SDIO WiFi)
4. Power on your device with charger unplugged. Wait till it reboots several times (about 5 minutes)
5. **Should be working!**

### In case of issues with display/sound/etc.

1. While device is off, connect it to your PC with a USB cable (use "OTG" port as we need data transfer)
2. Hold `Vol-` while booting, your device should enter recovery mode, and all storage should appear as USB drives to your PC
3. from ROCKNIX partition take `stock` directory and save it somewhere (*you may suddenly need it later in case of broken stock SD or wiped EMMC*)
4. there is a stock `whatever.dtb` file in `stock` dir. Upload it to [DTBO generator](https://rocknix.gosk.in/dtbo/) and experiment with options
5. put the `mipi-panel.dtbo` you get from the service to `overlays` folder
6. safely remove all the drives and boot your device with updated `dtbo` to see if the issue is fixed

### Flashing to EMMC

!!! info "EMMC is very slow to write and has a mediocre read speed too. Running from SD may be faster."
!!! danger "By trying this you can brick your device"

To unbrick, you may need to open the case and short some pads on PCB to skip EMMC boot. This needs understanding what the hell are you doing.

!!! warning "Be warned, we take no responsibility here"

1. As in previous section, Hold `Vol-` while booting to enter recovery mode and expose all storage to PC
2. **back up your `stock` directory** (or just dtb from there) (or dtb from EMMC, it's the same file). Really. You will need it later.
3. Flash the same `B` ROCKNIX image to EMMC (it's first of detected drives, usually 7.8 GB = 7.3 GiB in size). Remember to do `sync` after `dd` if you use it.
4. Copy your `stock` directory you backed up earlier to the new ROCKNIX partition of EMMC
5. safely remove all the drives
6. Remove ROCKNIX SD from your device and let it boot
7. **Should work now**
