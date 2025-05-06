# :material-hdmi-port: HDMI

## Setting up HDMI / DisplayPort-To-HDMI
Some devices support HDMI output to an external display.

To set the output resolution (eg to 1280x720) automatically on boot on a build using the sway compositor: 

Create autostart script:
```
mkdir /storage/.config/autostart
nano /storage/.config/autostart/090-sway-hdmi-resolution
```

In script (set a proper "output..." string to match your modifications):
```bash
#!/bin/bash
echo "output HDMI-A-1 resolution 1280x720" >> /storage/.config/sway/config
```

Common outputs are `HDMI-A-1` and `DP-1`. If your device does not have a dedicated HDMI port, it may use `DP-1`.

```bash
#!/bin/bash
echo "output DP-1 resolution 1920x1080" >> /storage/.config/sway/config
```

Make the script executable:
`chmod +x /storage/.config/autostart/090-sway-hdmi-resolution`

### Notes
Rocknix selects the output device at boot via the above script. If the chosen output is unavailable, Rocknix will use the primary display (your device). Some devices are currently unable to send an audio signal through HDMI. If your device's speakers are insufficient, consider using an aux cable with soundbar or a bluetooth speaker.
