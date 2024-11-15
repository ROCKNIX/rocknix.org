#  :material-update: Updating ROCKNIX

ROCKNIX can be updated "Over the Air" (OTA) or by manually downloading an update .tar file, adding to your device storage and rebooting.

## Option 1: OTA Update

If your device has access to the internet you can update ROCKNIX directly from EmulationStation.

1. In EmulationStation open the main menu by pressing the ++"Start"++ button on your controller.
2. Select `System Settings`
3. Scroll to the `System Update` header and select `Start Update`

!!! info "You can also view the change log for the latest release by selecting the `Change Log` before you update."

## Option 2: Manual Update

If you device does not have access to the internet you can still update manually

1. Download the latest update (.tar) of ROCKNIX for your device from the [releases page](https://github.com/ROCKNIX/distribution/releases/latest).
	* You'll find download links for each device/platform we support under the "`Update Package Downloads`" header.
    * Make sure to download the correct .tar file for your device.  For example; if you are installing ROCKNIX on a [Gameforce Ace](../devices/gameforce/gameforce-ace.md) you would download the `ROCKNIX-RK3588` file.
    * If you have any questions you can check the [Device Support](../devices/index.md) section to confirm which .tar you should download for your specific device.
2. Copy the update to the `/.update` folder located in the `STORAGE` partition of the OS SD card
4. Reboot the device, and the update will begin automatically.
