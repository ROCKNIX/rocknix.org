# :material-cloud-sync: Cloud Sync

ROCKNIX has built in support for multiple cloud sync options.  These can be used to sync save files, games and other files between multiple devices. 

## Syncthing

Syncthing is a tool that lets you synchronize the contents of folders across multiple devices. It is different from cloud storage in that devices are updated directly with the latest changes from their peer(s) whenever they are online at the same time.
Some things you can use it for with ROCKNIX:

* Keep your game library synchronized between your computer and ROCKNIX device(s),
* Keep all your handhelds synchronized (including those that run Android),
* Copy savegames as they are created and seamlessly continue playing on another device,
* Keep a copy of your configuration files for easier editing.

### Setup

#### Setup on ROCKNIX
* Make sure you are connected to a WiFi network before continuing.
* Go to "Network Settings" and set "Enable Syncthing" to "on". Make a note of your device's IP address, as well as the root password in the System Settings menu.
* On a computer or mobile device in the same network, open a browser and point it to "http://a.b.c.d:8384" where "a.b.c.d" is the IP address of your ROCKNIX device.
* When prompted for a user name and password, enter "root" as user and the password you noted earlier.
* You should now be directed to a configuration page running on your ROCKNIX device - we'll come back to this shortly.

#### Setup on Peer(s)

Install Syncthing on the device or computer that you want to synchronize with your ROCKNIX device. If your other device also runs ROCKNIX, simply repeat the above steps. Otherwise go to https://syncthing.net to download Syncthing for your platform. You may also find it in your Linux distribution's package manager, the Android Play Store, etc. Generally it is not required to install the same version of Syncthing on all devices. You can synchronize a folder across any number of peers.

#### Connecting Folders

1. Go to the web interface of your ROCKNIX device (see above). Don't worry about notices about upgrading or the file system being read-only, nothing you can do.
(Note: You can also go to the web interface of any of the peers, it'll work the same - but for this documentation it is assumed that you're on a ROCKNIX device.)
2. Under "Remote Devices", click "Add Remote Device". Enter the Device ID of the peer you want to synchronize with. If the remote is in the same network as your ROCKNIX device the ID will be shown automatically. Otherwise, you'll find it in the remote's web interface by clicking "Actions" at the top and then "Show ID". Give the device a name if you like.
3. In the "Folders" section, click "Add Folder". In the popup window that opens, set a label and specify the path on the device (e.g. /storage/roms). This is the folder you will be sharing with other peers.
4. In the same popup window, go to the "Sharing" tab and select the remote device you just set up. Optionally, go to the "Ignore Patterns" tab and configure those. Click "Save" to close the window.
5. On the remote's interface you should receive a popup that a new device wants to connect. Click "Add Device" and then "Save" to accept. It should now show up under "Remote Devices".
6. Still on the remote, you should receive a new popup saying that the ROCKNIX device wants to share a folder. Click "Add", then in the popup window, specify the path to an empty local folder to store the synchronized contents. Click "Save".
7. The folder should now be copied from the ROCKNIX device to the remote.

#### Adding more Peers

* To share the folder with more peers, first follow step 2 on your ROCKNIX device to add another remote.
* Find the folder you want to add another peer to and click "Edit".
* In the popup window, go to the "Sharing" tab. The new remote should appear as an option. Select it and then click "Save".
* Follow steps 5 and 6 on the new remote to connect the folder.

### Things to Keep in Mind

#### Syncthing is not a cloud storage
In order for devices to synchronize, they need to be online at the same time. Unless you have one peer that is always on, this is different from an online storage like Dropbox or Nextcloud. However, this behaviour can be emulated (no pun intended) by installing Syncthing on a cloud server or an always-on Raspberry Pi.

#### Syncthing is not a backup
Folders are synchronized with other peers immediately as they come online at the same time - this includes changes and deletions! Be sure to make regular backups of your folders.

#### Devices do not need to be on the same network
Syncthing uses relay servers to ensure communication between peers. This means that there does not need to be a direct connection between your devices, no port forwarding, etc - as soon as they are both online they will find each other and synchronize. Although file transfers are end-to-end encrypted when they are sent through relays, be aware of this if you plan on using Syncthing for anything more sensitive than your save files.

#### Using Syncthing for Saves/States
Using Syncthing for savegames is great because it allows you to seamlessly play a game across multiple handhelds, or even other devices. For example, you can play a game of Super Mario 64 on your RG353 while on the go, then launch the game on a RetroPie or PC running RetroArch and your save game will be transferred automatically to be continued on the big screen. However, this comes with a few caveats.

RetroArch differentiates between *saves*, i.e. the battery or memory card storage featured in the original game, and *states*, i.e. the save state feature that is part of the emulator. While *saves* are often compatible across different versions of RetroArch cores, *states* tend to break more frequently. This means that if you create states with two incompatible versions of an emulator and they are synchronized, you may lose one of them.

* For maximum compatibility, make sure to use the same cores on all devices and update them at similar frequencies.
* RetroArch uses two separate folders for *saves* and *states*. This makes it easy to choose whether you want to synchronize only saves, states, or both.
* In the RetroArch settings under "Saving", you can tell RetroArch to sort saves and states into subfolders based on content directory or core name. It is highly recommended to make use of this to reduce the risk of accidentally overwriting an incompatible save or state.
* Make regular backups of your save folders.

### Synchronizing with Android
* For Android-based handhelds people seem to be recommending the [Syncthing-Fork from F-Droid](https://f-droid.org/en/packages/com.github.catfriend1.syncthingandroid).
* Keeping Syncthing running in the background on Anroid may severely impact your battery life and reduce standby time. Check out [these tips](https://github.com/Catfriend1/syncthing-android/wiki/Info-on-battery-optimization-and-settings-affecting-battery-usage) to help you balance battery life and synchronization times.
* Using cross-platform versions of emulators is much more likely to introduce incompatibilities so be extra careful when syncing savegames.

### Further Documentation
For any questions and advanced configuration, be sure to check out the full documentation at https://docs.syncthing.net/index.html.


## Cloud Sync with rclone

ROCKNIX can keep your game saves in a cloud account and bring them back on any of your devices, using [rclone](https://rclone.org) underneath. You set it up on the device itself with the controller. You'll need a Wi-Fi connection and an account with a cloud provider (Dropbox, Google Drive, OneDrive, a WebDAV or S3 service, and others).

It keeps four kinds of thing apart, and the menus use these words throughout:

| What | What it covers | Where |
|---|---|---|
| **Saves** | game saves, save states, and screenshots | `Game Settings` → `Cloud Settings` |
| **Settings** | your configuration, as a backup archive: emulator and interface settings, controller mappings, themes, collections, bezels | `Manage Cloud Storage` → `Backup and Restore` |
| **ROMs and BIOS** | your games and BIOS files | `Manage Cloud Storage` → `Backup and Restore` |
| **Game content** | what the scraper made: artwork, videos, manuals, and the game lists | `Manage Cloud Storage` → `Backup and Restore` |

Saves move on their own once you turn that on. Everything else moves when you ask.

### Connecting your cloud storage

1. Press ++"START"++ → `Game Settings` → `Cloud Settings` → `Manage Cloud Storage`.
2. Under `Cloud Storage Setup`, select `Connect or Repair Cloud Storage`.
3. Pick your provider from the `Recommended` list, or open `More` for the rest. S3-style services ask which one first.
4. Fill in the form. Every provider asks for a name; the required fields are marked, the optional ones sit under their own heading. Select `Connect` under `Finish` when you're done. ROCKNIX tries the connection right away and only saves it if your provider answers.
    * Dropbox, Google Drive, and OneDrive sign you in instead of asking for a password. Choose `With the On-Screen Keyboard` to sign in on the device, or `With My Phone` to scan a code and type on your phone instead.
5. When you see `Cloud Setup Complete`, your cloud storage is ready. The `Connected To` row at the top of `Cloud Storage Setup` names it from then on.

<details> <summary>Screenshot: the provider list</summary>
  <img src="../../_inc/images/cloud-sync/connect-cloud-storage.png" />
</details>

!!! tip "If something stops working later, `Check Connection` on the same page says whether your cloud answers, and `Connect or Repair Cloud Storage` signs you in again without losing anything."

### The cloud folder

`Cloud Storage Setup` → `Change Cloud Folder` sets where ROCKNIX keeps everything on your provider. A new setup uses `/ROCKNIX`, with `Saves`, `Backups`, and `Content` folders inside it. Inside `Saves`, game saves stay under the system they belong to, and save states and screenshots keep their own folders.

!!! warning "Amazon S3, Backblaze B2, and other bucket storage"
    These services have no folders at the top level, only **buckets**, and the first part of the folder path is the bucket's name. Bucket names must be lowercase and are shared across everyone using the service, so `ROCKNIX` is refused. Set something unique to you, with the folders inside it: `/my-rocknix-saves`. ROCKNIX checks the name and won't accept one your provider can't use.

If you set ROCKNIX up before this layout existed, `Tidy Up Your Cloud Folders` appears on `Cloud Storage Setup` while there is something to move. It shows you what it would move first, and it is the one place that deletes anything in your cloud, so read the preview.

### Saves

`Game Settings` → `Cloud Settings` has three rows for saves, and each one shows how it last went underneath (`LAST <date> - COMPLETED`, or why it couldn't finish):

* `Sync Saves with the Cloud`: the newest copy of each save is kept on both sides. Nothing is deleted.
* `Back Up Saves to the Cloud`: this device's saves go up.
* `Restore Saves from the Cloud`: the cloud's saves come down.

<details> <summary>Screenshot: the saves rows under Game Settings</summary>
  <img src="../../_inc/images/cloud-sync/game-settings-cloud-rows.png" />
</details>

To have this happen by itself, go to `Manage Cloud Storage` → `Save Management` and turn on `Sync Saves During Startup` and `Sync Saves When Exiting a Game`. A small card at the top of the screen shows the sync running and how it ended. The one after a game takes a few seconds and waits for you; if you're offline it says `SKIPPED - YOU'RE NOT ONLINE` and tries again next time.

!!! note "Play on one console at a time"
    Sync assumes you play a game on one device, then pick it up on another, not both at once. If two devices have both changed the same save since they last agreed, ROCKNIX keeps the copy it is unsure about instead of throwing either away.

### Backing up and restoring the rest

`Manage Cloud Storage` → `Backup and Restore`:

<details> <summary>Screenshot: Manage Cloud Storage</summary>
  <img src="../../_inc/images/cloud-sync/cloud-hub.png" />
</details>

1. Select `Back Up to the Cloud` or `Restore from the Cloud`.
2. Tick what should move: `Saves`, `ROMs and BIOS`, `Game Content`, `Settings`. With `ROMs and BIOS` ticked, a page listing your systems comes next, with how much each would move, so you can pick a few.
3. Select `Back Up` (or `Restore`). With `ROMs and BIOS` ticked the button reads `Continue` instead, and the systems page comes first. The transfer then runs on its own page, with the file it's on and the time elapsed, and stays there when it's done so you can read how it went. `Cancel` is the way out while it runs; a cancelled transfer leaves what already arrived in place, and running it again picks up where it stopped.

<details> <summary>Screenshot: choosing what to back up</summary>
  <img src="../../_inc/images/cloud-sync/back-up-to-the-cloud.png" />
</details>

ROMs are large. Expect the first backup to take a while.

`Match This Device to the Cloud` makes the cloud's `ROMs and BIOS` folders mirror this device, deleting from the cloud what the device no longer has. It shows you exactly what it would delete before it does, and it is the only action in these menus that deletes anything.

!!! info "Passwords are never backed up"
    A settings backup leaves out your Wi-Fi password, your device password, and any account sign-ins, so an archive in your cloud never carries a credential. After you restore settings onto a device, `Finish Restore Process` appears under `Cloud Storage Setup` and walks you through re-entering them, Wi-Fi first.

### Backing up settings to the device itself

You don't need cloud storage for a settings backup. `System Settings` → `System Management and Reset` → `Data Management` has `Back Up Settings to This Device`, which writes the same archive to `/storage/roms/backup/`, and `Restore Settings from This Device`, which puts the newest one back and restarts. Copy the file somewhere safe afterwards; it's the same archive a cloud backup uploads, so one made here restores on any ROCKNIX device.

### Things to keep in mind

* A game save that changed but stayed the same size still reaches the cloud, on every kind of provider. Plain WebDAV servers keep neither file times nor checksums, so ROCKNIX compares the save's time on the device with its upload time there; a save written under a wrong clock waits for its next write.
* Saves you delete on the device are not deleted from the cloud, and the other way round. Only `Match This Device to the Cloud` deletes, and only under `ROMs and BIOS`.
* Everything ROCKNIX writes to your cloud stays under the cloud folder. It never touches anything else in your account.

### Troubleshooting

* `YOU'RE NOT ONLINE`: the device has no connection. Check `Network Settings`, then try again.
* `A SYNC IS ALREADY RUNNING`: wait for the card to finish, then try again.
* `COULDN'T REACH YOUR CLOUD. YOU MAY NEED TO SIGN IN AGAIN`: run `Check Connection`; if it doesn't answer, `Connect or Repair Cloud Storage` signs you in again.
* `YOUR CLOUD FOLDER WASN'T FOUND`: the folder under `Change Cloud Folder` no longer exists on your provider. Restoring saves offers to create it.

If you're comfortable with SSH, the sync writes what it did to `/var/log/cloud_sync.log`. If you run into anything else, share the details in the appropriate channel in Discord.

## NFS Storage

Create a file in '/storage/' called '.nfs-mount' containing a single line of the format:

```NFS_PATH=<Valid NFS URI>```

Navigate to 'Tools' and select 'Mount NFS' entry. The NFS path will be mounted to /storage/games-external and an overlay merge with /storage/games-internal as the upper will be created at /storage/roms. Saves/state will be written locally. 
