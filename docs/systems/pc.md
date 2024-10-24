# MS-DOS
## Overview

| Game Path | Supported Extensions |
| --- | --- |
| `roms/pc` | ++".com"++ ++".bat"++ ++".exe"++ ++".dosz"++ ++".zip"++ |

## Emulator/Core

| Name | Documentation |
| --- | --- |
| dosbox_pure &nbsp; `default` | [docs.libretro.com/library/dosbox_pure](https://docs.libretro.com/library/dosbox_pure/) |
| dosbox_svn | [docs.libretro.com/library/dosbox](https://docs.libretro.com/library/dosbox/) |

## Notes

If you are using the dosbox_pure core with `.dosz` or `.zip` roms, it will create libretro saves in the `roms/pc` directory with a `.pure.zip` extension. These save files capture changes to the original archive.

The `.pure.zip` files will appear in the EmulationStation game list. To prevent this, and store these in `/storage/roms/savestates/pc` instead, create a content directory override in `/storage/.config/retroarch/config/DOSBox-pure/pc.cfg` with content:

```
savefiles_in_content_dir = "false"
savefile_directory = "/storage/roms/savestates/pc"
```

After creating this content directory override, move any existing `.pure.zip` files into `/storage/roms/savestates/pc`.