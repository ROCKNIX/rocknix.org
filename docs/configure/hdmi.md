# :material-hdmi-port: HDMI

Some devices support HDMI output to an external display.

If your device supports HDMI, you should try to connect it to an HDMI display before following any other directions on this page. Configuring the HDMI display may not be necessary.

BEAR IN MIND that some devices may connect better with an HDMI display if the display is plugged into the device BEFORE the device is turned on

Below is how to set the output resolution (eg to 1280x720) on the external display automatically on boot using the sway compositor. These directions assume that you have used ssh to connect to the device. Alternatively you can remove the SD card, connect it to a computer and perform these same operations in a linux terminal, but you may need to type "sudo " before each command and put in the root password on your computer.

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

Optional: Force position to be 0 0

If you are still having trouble getting the external display to work correctly, you can force the external screen to mirror the device screen by following the above directions but instead using the code below in 090-sway-hdmi-resolution 

```
#!/bin/bash
echo "output HDMI-A-1 resolution 1280x720 position 0 0" >> /storage/.config/sway/config
```
