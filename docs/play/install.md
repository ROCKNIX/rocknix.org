# :material-progress-check: Installing ROCKNIX

ROCKNIX is installed by downloading an image for your device, flashing it to an SD Card (or your device's internal storage) and then booting the device to start the install process.

## Option 1: ROCKNIX Image Burner (Windows users)

* Download the latest version of the ROCKNIX Image Burner from the [releases page](https://github.com/ROCKNIX/ImageBurner/releases/latest).
* Select your manufacturer and device.
* Hit 'Write Image to Drive'.
* Continue to [Step 3](#step-3-boot-your-device).

## Option 2: Manually Download and Flash

### Step 1: Download [![Latest](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=111111&color=FF5555&label=Latest&style=flat#only-light)](https://github.com/ROCKNIX/distribution/releases/latest)[![Latest](https://img.shields.io/github/release/ROCKNIX/distribution.svg?labelColor=dddddd&color=FF5555&label=Latest&style=flat#only-dark)](https://github.com/ROCKNIX/distribution/releases/latest)

* Download the latest version of ROCKNIX for your device from the [releases page](https://github.com/ROCKNIX/distribution/releases/latest).
* You'll find download links for each device/platform we support under the "`Installation Package Downloads`" header.
* Make sure to download the correct image for your device.  For example; if you are installing ROCKNIX on a [Gameforce Ace](../devices/gameforce/gameforce-ace.md) you would download the `ROCKNIX-RK3588` image.
* If you have any questions you can check the [Device Support](../devices/index.md) section to confirm which image you should download for your specific device.

### Step 2: Flash

* First decompress the image.
* Then write the image to an SD Card using an imaging tool.
* Common imaging tools include [Rufus](https://rufus.ie/), [Raspberry Pi Imager](https://www.raspberrypi.com/software/), and [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/).  If you're skilled with the command line, `dd` can also be used.

### Step 3: Boot your device

* Insert your SD Card into your device while its off and then turn it on
* Note: Some devices may require you to set the boot order so your SD Card is loaded first.  Please see documentation for your specific device to see if this applies to you.
* ROCKNIX will run through its install process and then reboot your device after its complete.
* When your device reboots it will load directly into EmulationStation; at this point you are good to go!

---

## Additional Notes

* ROCKNIX operating system is stored on an Ext4 partition that can be read by LINUX but is not natively readable on Windows. Currently it is not possible to access the primary ROCKNIX Ext4 partition on Windows to add games.
* On devices that support a second sd card, the sd card can be formatted as Ext4, FAT32, or exFAT. ROCKNIX will automatically detect the second SD card on boot and make it available as game storage.
* On x86 devices ROCKNIX includes an installation tool.  The installation tool can be found in the tools menu, which is one of the systems listed within ES.

## Next Steps

* [Add Games](/play/add-games)
* [Set up Networking](/configure/networking)
* [Themes](/configure/themes)
