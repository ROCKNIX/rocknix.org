# id Tech Software

This system covers games using the id Software Doom, Quake, Quake 2 and Wolfenstein 3D engines.

## Game folders

Running the scrpt in `Tools` -> `Scan id Tech Files` before adding game files will create the following folder structure:
```
/storage/roms/idtech
├── doom
│   ├── doom
│   ├── doom2
│   ├── doomu
│   ├── plutonia
│   ├── sigil
│   ├── sigil2
│   ├── tnt
├── doom3
│   ├── base
│   ├── d3xp
├── quake
│   ├── dopa
│   ├── hipnotic
│   ├── id1
│   └── rogue
│   ├── malice
├── quake2
│   ├── baseq2
│   ├── rogue
│   ├── xatrix
│   └── zaero
├── quake3
│   ├── baseq3
└── wolf3d
    ├── sod
    └── wolf3d
```
## Adding Game Files

Following the above folder structure, these are the required files and naming for the scan script to populate. Be aware these aren't always the only files required for the emulator/core to run the game.

| Game | Folder | Game Files |
| --- | --- | --- |
| Doom | doom | doom.wad |
| Doom 2 | doom2 | doom2.wad | 
| The Ultimate Doom | doomu | doomu.wad |
| The Plutonia Experiment | plutonia | plutonia.wad |
| SIGIL | sigil | sigil.wad |
| SIGIL II | sigil2 | sigil2.wad |
| TNT Evilution | tnt | tnt.wad |
| Doom 3 | base | pak000.pk4 |
| Doom 3 - Resurrection of Evil | d3xp | pak000.pk4 |
| Quake | id1 | pak0.pak |
| Quake - Scourge of Armagon | hipnotic | pak0.pak |
| Quake - Dissolution of Eternity | rogue | pak0.pak |
| Quake - Dimension of the Past | dopa | pak0.pak |
| Malice | malice | pak0.pak |
| Quake 2 | baseq2 | pak0.pak |
| Quake 2 - The Reckoning | xatrix | pak0.pak |
| Quake 2 - Ground Zero | rogue | pak0.pak |
| Quake 2 - Zaero | zaero | pak0.pak |
| Quake 3 | baseq3 | pak0.pk3 |
| Wolfenstein 3D | wolf3d | vswap.wl6 |
| Wolfenstein 3D - Spear of Destiny | sod | vswap.sod |

## Launcher scripts

Run `Tools` -> `Scan id Tech Files` to create launch scripts, and EmulationStation should restart automatically and populate the gamelists. If you don't see the id Tech system in ES, then rescan gamelists, restart EmulationStation, or reboot the unit. This can be re-run at any time should you add additional game files.

## Emulator/Core

| Name | Documentation |
| --- | --- |
| prboom | [docs.libretro.com/library/prboom](https://docs.libretro.com/library/prboom) |
| boom3<br/>boom3_xp | [docs.libretro.com/library/boom3](https://docs.libretro.com/library/boom3) |
| tyrquake | [docs.libretro.com/library/tyrquake](https://docs.libretro.com/library/tyrquake) |
| vitaquake2<br/>vitaquake2-xatrix<br/>vitaquake2-rogue<br/>vitaquake2-zaero | None available |
| ecwolf | [docs.libretro.com/library/ecwolf](https://docs.libretro.com/library/ecwolf) |

## NOTE

Doom3 and Quake3 are only for x86-64 based devices.

Doom ShareWare will be preinstalled after running `Tools` -> `Scan id Tech Files`.
