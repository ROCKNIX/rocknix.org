# :material-sleep: Fake Suspend

## Overview

Fake suspend is available on platforms that do not support hardware suspend and resume. This allows the device to enter a short term low power state, with a configurable shutdown delay.

Fake suspend can be activated by pressing the power button or closing the lid on clamshell devices. The following configurable actions are performed:

- LEDs are disabled
- audio is muted
- controls are disabled (besides lid / power button)
- display or backlight is turned off
- game / EmulationStation processes are frozen
- CPU / GPU governors are set to powersave
- CPU cores 1...n are brought offline, core 0 left online
- a shutdown delay timer begins

If a game is running when fake suspend is triggered, it will continue to run in a low power state, allowing quick gameplay resume.

When the power button is pressed again, or the lid is opened on clamshell devices, the following actions are performed as required:

- CPU cores 1...n are brought back online
- CPU / GPU governors are restored to their pre-suspend value
- game / EmulationStation processes are woken
- display or backlight is turned on
- controls are enabled
- audio is unmuted
- LEDs are enabled
- the shutdown delay timer is cancelled

If the shutdown delay timer expires before resume is triggered, the device will shut down.

## Configuration

Behaviour can be configured in the EmulationStation 'System Settings' menu, 'Suspend' section menu.

### Enable suspend

This setting is a global toggle for fake suspend. If it is disabled, pressing the power button or closing the lid will have no effect.

### Enable timed shutdown

This setting controls whether a timed shutdown will be triggered after suspending. If it is disabled, the device will remain suspended until the battery dies.

### Shutdown delay

This setting controls how long fake suspend is active (0 - 30 minutes: default 0 minutes) before a timed shutdown occurs, when *not* in-game. If the delay is set to 0 minutes, shutdown will occur immediately.

### Shutdown delay (in game)

This setting controls how long fake suspend is active (0 - 30 minutes: default 15 minutes) before a timed shutdown occurs, when in-game. If the delay is set to 0 minutes, shutdown will occur immediately.

### Enable core parking

This setting controls whether or not CPU cores 1...n are brought offline during fake suspend. Process affinity settings are lost when cores are brought offline, so disable this if you depend on core pinning, for example pinning an emulator to little cores to save battery, or to big cores for better performance.

### Enable DPMS

This setting controls whether the display is turned off using window manager DPMS or using simple backlight control. It can cause instability issues on some platforms, so is disabled by default. However it can be enabled on an opt-in basis if it works fine on your device.

## Charging

If a charger connection is detected, the suspend actions are triggered, but no shutdown will be performed.

This is intended to enable charging while in a low-power state - connect a charger, then tap power or close the lid.

!!! note "Most of the supported devices will boot up again when shut down with a charger connected, but this time not in a low power state which defeats the purpose of fake suspend."

## HDMI

If you have a HDMI cable connected, the suspend actions and shutdown delay are not triggered.

This is intended to enable 'docking' clamshell devices with the lid closed.

!!! note "Video out via USB-C DP Alt Mode is not currently detected, only HDMI."
