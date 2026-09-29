# :material-wifi-plus: Networking

Networking can be set up on any device that can connect to the internet (this includes devices with native networking capabilites and ones where networking can be added through an external dongle).  

With networking turned on you do things such as [add games](../../play/add-games), [update ROCKNIX](../../play/update), [netplay across devices](../../play/netplay), [cloud sync](../cloud-sync), [play over VPN](../vpn) and access [RetroAchievements](../../play/retro-achievements/).

## Setup

1. While in EmulationStation press ++"START"++ on your controller to open the Main Menu.
2. Navigate to and select `Network Settings`.
3. Under the Settings header turn on `Enable Wi-Fi`.
4. Select `Wi-Fi Network`. ROCKNIX looks for the networks around you and lists them; pick yours.
5. Type the password on the onscreen keyboard.

ROCKNIX connects while you wait, and the `Wi-Fi Network` row names your network from then on. If it can't connect it tells you why, and you can try the password again.

<details> <summary>Screenshot: Network Settings</summary>
  <img src="../../_inc/images/networking/network-settings.png" />
</details>
<details> <summary>Screenshot: the list of Wi-Fi networks</summary>
  <img src="../../_inc/images/networking/wifi-networks.png" />
</details>

## Networks you've joined before

ROCKNIX keeps the password of every network you join, so it reconnects on its own next time. In the list, a network you've joined carries a `SAVED` mark and the one you're on reads `CONNECTED`.

- Selecting a saved network asks whether to `Connect` with the saved password or `Forget` it. Forget it when the password has changed, then join it again with the new one.
- `Manage Saved Networks`, under `Wi-Fi Network`, lists everything ROCKNIX has kept. Select a network there to forget it.
- A network that hides its name is added with `Input Manually` at the bottom of the list: type the name, then the password.

<details> <summary>Screenshot: a saved network, selected</summary>
  <img src="../../_inc/images/networking/wifi-saved-network.png" />
</details>
<details> <summary>Screenshot: Manage Saved Networks</summary>
  <img src="../../_inc/images/networking/saved-networks.png" />
</details>
<details> <summary>Screenshot: forgetting a network</summary>
  <img src="../../_inc/images/networking/forget-network.png" />
</details>

!!! note "Wi-Fi passwords stay on the device"
    A settings backup to the cloud leaves them out, so after you restore settings onto another device, join your network again there.

## Additional Notes

- If you want to transfer games over the network make sure to turn enable SSH and Samba under `Network Services`.  You can read more about that on the [Add Games](../../play/add-games) page.
- If you want to enable netplay to be able to play multiplayer across devices please see the page on [Netplay](../../play/netplay).
- Check out [Cloud Sync](../cloud-sync) to see the available options and steps for setting up cloud sync services.
- If you would like to earn achievements while playing games please check out [RetroAchievements](../../play/retro-achievements/)
- If you have pre-existing collections you can use NFS(Network File System) to mount an NFS share which will be merged with the internal storage to quickly access pre-curated collections instantly(sometimes refered to as streaming) see [Add Games](../../play/add-games)
