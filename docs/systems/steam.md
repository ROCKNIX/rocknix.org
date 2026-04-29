# Steam

ROCKNIX supports Steam (arm64), allowing you to run native Linux games as well as Windows games using FEX + Proton (x86) and Proton (arm64).

## Step 1: Install Steam in ROCKNIX
Steam needs to be installed first from Tools by selecting "Install Steam". During the first installation, ROCKNIX will download the FEX Arch rootfs and install the Steam runtime and its dependencies.

After the installation is complete, Steam will appear in the main EmulationStation menu.

!!! tip "Installing ROCKNIX to internal memory significantly decreases Steam startup time, as well as game installation and launch times. Therefore, using ROCKNIX from internal memory is recommended for the best performance."

## Step 2: Configure Steam in ROCKNIX
Launch Steam from EmulationStation and sign in with your Steam account.

After successfully logging in, a second "Steam storage" location will be created under `/roms/steam`. You can copy games from your PC's Steam library there if you do not want to download them again from the Internet.

Custom Proton versions can also be installed by copying them to `/storage/.steam/root/compatibilitytools.d`

!!! tip "To use Proton 11 (arm64), open Steam and search for Proton 11 ARM64. Download it to the default Steam directory (~/.local/share/Steam/steamapps/common/).
Currently, Steam does not install this automatically."

### Controller Support
The controller works in games after enabling Steam Input. To enable Steam Input, select the game, click the controller icon (to the right of the 'Play' button), and click "Enable Steam Input".

### Performance Options (x86 proton only)
You can enable host libraries (DRM, Vulkan, GL) in EmulationStation advanced system options to increase performance and reduce input lag. However, this may prevent some games from launching or, in some cases, may fix games that would otherwise fail to start.

## Step 3: Play
Install or copy your games, then launch them from Steam as usual.

Any game installed by Steam will also appear in the EmulationStation menu under Steam.

## Compatibility Notes
* Games which require RTX may not work.
* Rocknix Steam Compability DB: [RocknixDB]https://rocknix-steamdb.pages.dev/
* Many useful game-specific compatibility notes and launch tweaks can be found on [ProtonDB](https://www.protondb.com/).
* For some DirectX 12 games that do not boot, try adding the following to the game's launch arguments:

```text
VKD3D_FEATURE_LEVEL=12_1 %command%
```

* For Helldivers 2, the following launch arguments may help:

```text
DXVK_CONFIG="dxvk.enableAsync = true; dxvk.gplAsyncCache = true; dxvk.enableGraphicsPipelineLibrary = false; d3d11.cachedDynamicResources=vi; d3d11.maxFeatureLevel = 12_1" %command% -use-d3d11
```

* Counter-Strike 2 requires enabling the DRM, Vulkan, and Wayland client host libraries in EmulationStation advanced system options.


## Toogle between steam (x86) and (arm64)
In the EmulationStation advanced settings menu, there is an option to switch between Steam versions (x86 and arm64).
Use this setting to easily toggle which version of Steam is launched.
 




