# :octicons-stack-16: Building ROCKNIX locally

ROCKNIX is a fairly unique distribution as it is *built to order* and only enough of the operating system and applications are built for the purpose of booting and executing emulators and ports.  Developers and others who would like to contribute to our project should read and agree to the [Contributor Code of Conduct](code-of-conduct.md) and [Contributing to ROCKNIX](index.md) guides before submitting your first contribution.

## 1. Prep

Building ROCKNIX requires a host with 200GB of free space for a single device, or 1TB of free space for a full world build.  

!!! note "Expect your first build to take on the order of ten hours.  You will need a stable internet connection, since hundreds of packages will be downloaded from their source."  

Download errors often produce build failures with misleading error messages.  If this happens to you, see the Troubleshooting section below.

After a clean build, all subsequent builds will go much faster (minutes) since 99% of the build work is cached.

### Docker **(Recommended)**

!!! tip "Docker is the easiest and most reliable way to build ROCKNIX." 

You need no previous experience with Docker; you merely need to install it on your build machine.  Newcomers to the project are strongly recommended to use this approach.

We recommend using Ubuntu 22.04 for the host machine, as this is well-tested and known to work.  Other distributions and operating systems might also work for Docker builds, but are untested and unsupported.

``` bash title="Install Docker using the following commands:"
sudo apt update
sudo apt install ca-certificates curl gnupg

sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker

docker run hello-world
```

> Docker installation reference (source): [Install using the apt repository](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) and [Linux post-installation steps](https://docs.docker.com/engine/install/linux-postinstall/).

The final command should produce a message indicating that Docker is properly installed.  If you encounter any errors, see the reference links above.

### Manual Build

Manual builds (outside of Docker) are only recommended for developers with specific needs that cannot be met by the Docker approach.  The host configuration should match the Docker container as closely as possible, running Ubuntu 22.04 with all packages listed in the [Dockerfile](https://github.com/ROCKNIX/distribution/blob/main/Dockerfile).

### Virtual Machines

If you prefer to use a virtual machine for your build platform; keep in mind that results vary. There have been some reports of success with VMware Workstation (Player and Pro) and WSL and some unsuccessful attempts with VirtualBox. These reports are not definitive, but something to keep in mind if you prefer to use a VM.

## 2. Clone

After preparing the build machine, clone the ROCKNIX git repository onto it.

``` bash
cd ~
git clone https://github.com/ROCKNIX/distribution.git
```

### Selecting the Desired Branch

Once you have cloned the repo, decide whether you want to build the main branch which is more stable, or the development branch which is unstable but hosts our newest features.

|Branch|Purpose|
|----|----|
|main|Stable ROCKNIX sources|
|dev|Unstable ROCKNIX sources|

To check out our development branch, cd into the project directory and checkout `dev`.

``` bash
cd distribution
git checkout dev
```

### Filesystem Structure
We have a simple filesystem structure adopted from parent distributions CoreELEC, LibreELEC, etc.

``` bash
.
├── build.ROCKNIX-DEVICE.ARCHITECTURE
├── config
├── distributions
├── Dockerfile
├── licenses
├── Makefile
├── packages
├── post-update
├── projects
├── release
├── scripts
├── sources
└── tools
```

**build.ROCKNIX-DEVICE.ARCHITECTURE**

Build roots for each device and that device's architecture(s).  For ARM devices ROCKNIX builds and uses a 32bit root for several of the cores used in the 64bit distribution.

**config**

Contains functions utilized during the build process including architecture specific build flags, optimizations, and functions used throughout the build workflow.

**distributions**

Distributions contains distribution-specific build flags and parameters and splash screens.

**Dockerfile**

Used to build the Ubuntu container used to build ROCKNIX.  The container is hosted at [https://hub.docker.com/u/rocknix](https://hub.docker.com/u/rocknix).

**licenses**

All of the licenses used throughout the distribution packages are hosted here.  If you're adding a package that contains a license, make sure it is available in this directory before submitting the PR.

**Makefile**

Used to build one or more ROCKNIX images, or to build and deploy the Ubuntu container.

**packages**

All of the packages used to develop and build ROCKNIX are hosted within the packages directory.  The package structure documentation is available [here](packages.md).

**post-update**

Anything that is necessary to be run on a device after an upgrade should be added here.  Be sure to apply a guard to test that the change needs to be executed before execution.

**projects**

Hardware-specific parameters are stored in the projects folder.  Anything that should not be included on every device during a world build should be isolated to the specific project or device here.

**release**

The output directory for all of the build images.

**scripts**

This directory contains all of the scripts used to fetch, extract, build, and release the distribution.  Review Makefile for more details.

**sources**

As the distribution is being built, package source files are fetched and hosted in this directory.  They will persist after a `make clean`.

**tools**

The tools directory contains utility scripts that can be used during the development process, including a simple tool to burn an image to a usb drive or sdcard.

## 3. Build

### Making the Builder image

To be able to build with Docker, you'll need to create the builder image. This only needs to be done one time before you build your first image.

``` bash
make docker-image-build
```
!!! note "For users with docker <= 22, the BuildKit plugin must also be installed. You can alternatively build using the legacy builder with `docker build --tag "rocknix/rocknix-build:latest" .`"  

### Building Device Images

Building ROCKNIX is easy.  From the root of your local repository, issue one of the `make` commands listed below, depending on the desired device and whether you are using Docker.

| Devices | Dependency | Docker Command | Manual Command |
| ---- | ---- | ---- | ---- |
|RK3588||`make docker-RK3588`|`make RK3588`|
|RK3326||`make docker-RK3326`|`make RK3326`|
|RK3566||`make docker-RK3566`|`make RK3566`|
|S922X||`make docker-S922X`|`make S922X`|
|ALL DEVICES||`make docker-world`|`make world`|

> Devices that list a dependency require you to build the dependency first, since that build will be used as the root of the device you are building.

For example, the following command uses Docker to build the RK3588 image.  

``` bash
make docker-RK3588
```

### Rightsized Builds

ROCKNIX supports various build variables which alter the behavior of the distribution for specific purposes including debugging, or hosting containers.  The options are defined below and are passed on the make command line.  Ex. `BASE_ONLY=true make docker-RK3566`.

|Build Option|Default|Function|
|----|----|----|
|EMULATION_DEVICE|yes|Builds EmulationStation and all emulators if `yes`. Builds EmulationStation and NO emulators if `no`.|
|ENABLE_32BIT|yes|Builds a 32bit root and includes it in the image.  Needed for 32bit cores and applications.|
|BASE_ONLY|false<sup>1</sup>|Builds only the bare minimum packages.  Includes Sway or Weston on supported devices.  Does not build EmulationStation.|
|CONTAINER_SUPPORT|no|Builds support for running containers on ROCKNIX.|

> Note: <sup>1</sup> this property will change to yes/no for consistency in a future release.

### Env Variables

For development builds, you can use the following env variables to customize the image or change build time functionality. To make them globally available to the builds, add them to `${HOME}/.ROCKNIX/options`.

|Variable|Function|
|----|----|
|LOCAL_SSH_KEYS_FILE|Enables using ssh public keys for access without the root password.|
|LOCAL_WIFI_SSID|The SSID of the network the device should connect to automatically.|
|LOCAL_WIFI_KEY|The WIFI authentication key for the connection."|
|SCREENSCRAPER_DEV_LOGIN|Login information for screenscraper.fr.|
|GAMESDB_APIKEY|Login information for thegamesdb.net.|
|CHEEVOS_DEV_LOGIN|Login information for retroachievements.org.|
|CLEAN_PACKAGES|Allows specifying packages to clean during a build.|
|CONCURRENCY_MAKE_LEVEL|The number of concurrent jobs to use during a build (defaults to the number returned by `nproc`).|

#### SSH Keys

``` bash
export LOCAL_SSH_KEYS_FILE=~/.ssh/rocknix/authorized_keys
```

#### WiFi SSID and password

``` bash
export LOCAL_WIFI_SSID=MYWIFI
export LOCAL_WIFI_KEY=secret
```

#### Screenscraper, GamesDB, and RetroAchievements

To enable Screenscraper, GamesDB, and RetroAchievements, register at each site and apply the api keys in `${HOME}/.ROCKNIX/options`. Unsetting one of the variables will disable it in EmulationStation. This configuration is picked up by EmulationStation during the build.

``` bash
# Apply for a Screenscraper API Key here: https://www.screenscraper.fr/forumsujets.php?frub=12&numpage=0
export SCREENSCRAPER_DEV_LOGIN="devid=DEVID&devpassword=DEVPASSWORD"
# Apply for a GamesDB API Key here: https://forums.thegamesdb.net/viewforum.php?f=10
export GAMESDB_APIKEY="APIKEY"
# Find your Cheevos Web API key here: https://retroachievements.org/controlpanel.php
export CHEEVOS_DEV_LOGIN="z=RETROACHIEVEMENTSUSERNAME&y=APIKEYID"
```

### Cleaning Additional Packages

``` bash
make docker-shell
CLEAN_PACKAGES="linux ppsspp-sa" make RK3588
exit
```
The first and last lines should be omitted if building outside of Docker.

## Troubleshooting

The very first build after a fresh checkout is the hardest. Give yourself sufficient time to generate the first build and work through any failures before attempting to modify ROCKNIX. 

Download errors can produce misleading failure messages so beware of chasing red herrings.  A network failure is much more likely than a bug in the makefile, given how frequently it is tested by our CI system and other devs.

### Option 1: Clean the package that failed

Try cleaning the failed package and building again using the following command:
``` bash
PROJECT={PROJECT} DEVICE={DEVICE} ARCH={ARCH} ./scripts/clean {PACAKGE NAME}
```

Use this table to determine the values you should use in the above command:

| For Build | PROJECT | DEVICE | ARCH |
| ---- | ---- | ---- | ---- |
| RK3588 | Rockchip | RK3588 | aarch64 |
| RK3326 | Rockchip | RK3326 | aarch64 |
| RK3566 | Rockchip | RK3566 | aarch64 |
| RK3566-X55 | Rockchip | RK3566-X55 | aarch64 |
| S922X | Amlogic | S922X | aarch64 |

As an example; if you were buildling `RK3588` and wanted to clean the `mame-lr` package:
``` bash
PROJECT=Rockchip DEVICE=RK3588 ARCH=aarch64 ./scripts/clean mame-lr
```

After cleaning a package you can try to build/install it directly as a quick way to see if the error is resolved.  Just change the script to `install` or `build` depending on what the package requires.

Using our example above (e.g. building for RK3588) mame-lr requires `install` so you can run this command to check it directly
``` bash
PROJECT=Rockchip DEVICE=RK3588 ARCH=aarch64 ./scripts/install mame-lr
```

If that completes without error then running the build for your device should proceed.

### Option 2: Delete the source of the package that failed

If you are still getting an error after trying the above its likely that a download failure occured for the source of the package that is failing. 

In this case; manually delete the relevant package(s) from the `sources` and `build.ROCKNIX-...` directories and start your build again.  This will force that package to be re-downloaded from source and re-built.

### Additional notes
- In most cases build failures are caused by single package failures which the above options should help resolve. Exhaust all options before using `make clean` for the entire build. That action will delete the build cache and takes hours to regenerate.  
- As a very last resort, delete the entire local repository and start over. This is VERY rarely needed so please focus on the above options first.
