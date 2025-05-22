---
search:
  exclude: true
---

# Retroid Pocket Mini

![](../../_inc/images/devices/retroid-pocket-mini.png){ .off-glb }

## Overview

| Device | CPU / Architecture | Kernel | GL driver | Vulkan driver | Interface |
| -- | -- | -- | -- | -- | -- |
| Retroid Pocket Mini | Qualcomm SD865 (SM8250) | Mainline Linux | Freedreno | Turnip | Sway + Emulation Station |

## Features

| Feature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Notes |
| -- | -- |
| :material-wifi: Wifi | Can be turned on in Emulation Station under Main Menu > Network Settings |
| :simple-bluetooth: Bluetooth | Supports bluetooth audio and controllers |
| :material-fan: Fan | Can be set globally, per system or per game. |
| :material-lightbulb-on: Joystick LEDS | Supports selecting from a set of colors, battery level status, <br>  or turning the joystick LEDS off. |
| :material-vibrate: Rumble | Can be turned on or off in Emulation Station under <br> Controller & Bluetooth Settings > Enable Rumble |

## Controls

{%set btn_north = 'X(NORTH)' %}
{%set btn_west = 'Y(WEST)' %}
{%set btn_south = 'B(SOUTH)' %}
{%set btn_east = 'A(EAST)' %}
{%set btn_hotkey_a = 'HOME' %}

{%include 'controls/extra.md' %}
{%include 'controls/retroarch.md' %}
{%include 'controls/mupen64plus.md' %}
{%include 'controls/ppsspp.md' %}
{%include 'controls/dolphinqt.md' %}
{%include 'controls/dolphin.md' %}
{%include 'controls/aethersx2.md' %}
{%include 'controls/xemu.md' %}
{%include 'controls/duckstation.md' %}
{%include 'controls/lime3ds.md' %}
{%include 'controls/azahar.md' %}

## Additional References

- [Platform Documentation (SM8250)](https://github.com/ROCKNIX/distribution/blob/main/documentation/PER_DEVICE_DOCUMENTATION/SM8250)

### Screen issue
!!! note "If you have screen issues, you likely didn't choose a proper entry during boot"
    ![](../../_inc/images/devices/retroid-pocket-mini-inverted.png){ .off-glb }
    To fix broken image you need to:

     * flash a working loader (seen next section about Bootloader, GRUB and fastboot)
     * on boot, select a boot entry which corresponds to your device

### Retroid Pocket Mini V2

!!! note "Retroid's Android OTA for the Pocket Mini V2 Breaks Bootloader Visibility"
    The latest OTA update from Retroid for the Pocket Mini V2 includes a faulty bootloader. 
    As a result, the GRUB boot selection screen is no longer visible at startup.

    #### How to Fix It
    You’ll need to manually reflash the **loader partition** using **fastboot**.

    #### Step 1: Install Fastboot Tools
    [15-Second ADB/Fastboot Installer](https://xdaforums.com/t/official-tool-windows-adb-fastboot-and-drivers-15-seconds-adb-installer-v1-4-3.2588979/)

    #### Step 2: Download the Fixed Bootloader
    [Download u-boot-sm8250-retroidpocket-rpminiv2.img](https://github.com/RetroidPocket/u-boot/releases/download/rp-v1.0.1/u-boot-sm8250-retroidpocket-rpminiv2.img)

    #### Step 3: Enter Fastboot Mode
    Hold **Volume Down** while powering on the device.

    #### Step 4: Flash the Loader Partition
    ```
    fastboot flash loader u-boot-sm8250-retroidpocket-rpminiv2.img
    ```

### Community Videos

| <iframe width="560" height="315" src="https://www.youtube.com/embed/PtZKzzWysw8?si=Zg8OB4gFO9aRG0Hb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> |
