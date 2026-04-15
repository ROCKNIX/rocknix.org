# Steam

ROCKNIX supports Steam, allowing you to run native Linux games as well as Windows games through Proton.

## Step 1: Install Steam in ROCKNIX
Steam needs to be installed first from Tools by selecting "Start Steam". During the first installation, ROCKNIX will download the FEX Arch rootfs and install the Steam runtime and its dependencies.

After the installation is complete, Steam will appear in the main EmulationStation menu.

!!! tip "Installing ROCKNIX to internal memory significantly decreases Steam startup time, as well as game installation and launch times. Therefore, using ROCKNIX from internal memory is recommended for the best performance."

## Step 2: Configure Steam in ROCKNIX
Launch Steam from EmulationStation and sign in with your Steam account.

After successfully logging in, a second "Steam storage" location will be created under `/roms/steam`. You can copy games from your PC's Steam library there if you do not want to download them again from the Internet.

Custom Proton versions can also be installed by copying them to `/storage/.steam/root/compatibilitytools.d`

### Controller Support
The controller works in games after enabling Steam Input.

### Performance Options
You can enable host libraries (DRM, Vulkan, GL) in EmulationStation advanced system options to increase performance and reduce input lag. However, this may prevent some games from launching or, in some cases, may fix games that would otherwise fail to start.

## Step 3: Play
Install or copy your games, then launch them from Steam as usual.

Any game installed by Steam will also appear in the EmulationStation menu under Steam.

## Step 4: Compatibility Notes
* Games which require RTX may not work.
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



