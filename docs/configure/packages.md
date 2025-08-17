# :material-package-down: Managing packages

## Entware

[Entware](https://github.com/Entware/Entware/wiki) is a modern alternative to Optware and was originally designed for use on OpenWRT but has been adapted for use on other distributions, it is similar to apt/yum/pacman in that it will allow you to install over 2000+ Linux applications.

### Install

1. SSH into your device
2. Run `installentware`
3. Reboot after that completes

### Command-line instructions

You can manage packages  over ssh using the command-line interface.

| Command&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Description |
| -- | -- |
| `opkg update` | Fetch a list of available packages from the OpenWrt package repository. |
| `opkg list` | Display a list of available packages and their descriptions. |
| `opkg list | grep -e <search>` | Filter the list by a search term in the package name or its description. |
| `opkg install <packages>` | Install a package. |
| `opkg remove <packages>` | Uninstall a previously installed package. |