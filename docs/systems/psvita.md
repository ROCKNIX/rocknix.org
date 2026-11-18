# Sony PlayStation Vita

## Overview

| Game Path | Supported Extensions |
| -- | -- |
| `roms/psvita` | ++".pkg"++ ++".psvita"++ ++".zip"++ |

## Emulator/Core

| Name | Documentation |
| --- | --- |
| Vita3K+ (default) | [Vita3K+ on GitHub](https://github.com/nckstwrt/Vita3K-Plus) |
| Vita3K | [vita3k.org/quickstart.html](https://vita3k.org/quickstart.html) |

Vita3K+ was added to the main ROCKNIX repository in [PR #3587](https://github.com/ROCKNIX/distribution/pull/3587) and is now the default emulator for Vita. It has better game compatibility than Vita3K.

## Bios

> Path: `roms/bios/vita3k`

| Emulator | Required Files |
| -- | -- |
| Vita3K+/Vita3K | `PSVUPDAT.PUP`, `PSP2UPDAT.PUP` |

- Put both `.PUP` files in `roms/bios/vita3k`, then run **Start Vita3K+** from the Tools menu. They will be installed automatically.

## Notes

- Running a `.pkg` or `.zip` game installs it but doesn't launch it. Close the emulator, then start the game from the `.psvita` file that is created.
- `.pkg` games also need a `.txt` file with the same name that contains the ZRIF.
- You can delete the `.pkg` or `.zip` file after installation to save space.
- Both emulators use the same game folder, so a game installed with one works with the other.
- Config folders live under `/storage/.config`: Vita3K+ uses `vita3kplus` and Vita3K uses `vita3k`. If you changed Vita3K settings before this update, move your `config.yml` into `/storage/.config/vita3k/` to keep them.
