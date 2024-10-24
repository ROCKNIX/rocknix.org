# :material-hdmi-port: HDMI

Some devices support HDMI output to an external display.

To set the output resolution (eg to 1280x720) automatically on boot on a build using the sway compositor: 

Create autostart script:
```
mkdir /storage/.config/autostart
nano /storage/.config/autostart/090-sway-hdmi-resolution
```

In script (set a proper "output..." string to match your modifications):
```
#!/bin/bash
echo "output HDMI-A-1 resolution 1280x720" >> /storage/.config/sway/config
```

Make the script executable:
```
chmod +x /storage/.config/autostart/090-sway-hdmi-resolution
```