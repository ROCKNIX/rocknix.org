---
title: Anbernic H700 installation guide
search:
  exclude: true
---

# Anbernic H700 installation guide

Anbernic H700 devices installation requires some manual steps to do after flashing a new image and before booting the device.
These steps are only to be done once, and are not needed for regular updates.

## Copy the correct .dtb file for your device
Each H700 device needs its corresponding DTB to be copied in the root folder of the **ROCKNIX** partition.
Here is the name of the files to use.
!!! warning "the RG35XX line have two versions of the DTB depending on your device PCB revision, it's impossible to know the difference (without opening the device) so you'll have to try. If the screens display garbage, **shut it down** (10s long press on power), reflash and try the other DTB file."
|Model|DTB|
|----------------|-------------------------------|
|RG28XX|`sun50i-h700-anbernic-rg28xx.dtb`|
|RG34XX |`sun50i-h700-anbernic-rg34xx.dtb`            |
|RG34XX SP |`sun50i-h700-anbernic-rg34xx-sp.dtb`            |
|RG35XX 2024|`sun50i-h700-anbernic-rg35xx-2024.dtb`|
|RG35XX 2024 rev6|`sun50i-h700-anbernic-rg35xx-2024-rev6-panel.dtb`|
|RG35XX H|`sun50i-h700-anbernic-rg35xx-h.dtb`|
|RG35XX H rev6|`sun50i-h700-anbernic-rg35xx-h-rev6-panel.dtb`|
|RG35XX Plus|`sun50i-h700-anbernic-rg35xx-plus.dtb`|
|RG35XX Plus rev6|`sun50i-h700-anbernic-rg35xx-plus-rev6-panel.dtb`|
|RG35XX Pro|`sun50i-h700-anbernic-rg35xx-pro.dtb`|
|RG35XX SP|`sun50i-h700-anbernic-rg35xx-sp.dtb`|
|RG35XX SP v2|`sun50i-h700-anbernic-rg35xx-sp-v2-panel.dtb`|
|RG40XX H|`sun50i-h700-anbernic-rg40xx-h.dtb`|
|RG40XX V|`sun50i-h700-anbernic-rg40xx-v.dtb`|
|RG CubeXX|`sun50i-h700-anbernic-rgcubexx.dtb`|

All the DTB files are located in the folder `device_trees` of the **ROCKNIX** partition.
Locate your DTB and copy it in the root of of the **ROCKNIX** partition.

## Rename the DTB file

Once the correct DTB file has been copied in the root of the **ROCKNIX** partition, you need to rename it to `dtb.img` (all lowercase).

## Eject SD and boot ROCKNIX

Properly eject your SD card by using your OS **Eject** function. Skipping this step may render your SD card unbootable, and you'll have to reflash it with the image and redo these steps from the start.
Insert your SD card in your device and power it up
Done.
