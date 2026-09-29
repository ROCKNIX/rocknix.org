# :material-cog-outline: Cloud sync and offline achievements, underneath

The [Cloud Sync](../configure/cloud-sync/) and [RetroAchievements](../play/retro-achievements/) pages say what to press. This page says what runs underneath, where it writes, and why I built it that way, for anyone reading the scripts or reviewing the pull requests. Each section names the script or source file it describes. Every path is on the device.

The `D-…` references are rows in the decision register on my fork ([maxengel/rocknix, docs/decision-register.md](https://github.com/maxengel/rocknix/blob/next/docs/decision-register.md)), where each choice was recorded when it was made.

## The four tiers and their folders

The interface and the scripts move four kinds of thing and keep them apart (D-UI-022): **saves** (game saves, save states, screenshots), **settings** (the archive `backuptool` writes), **ROMs and BIOS**, and **game content** (what the scraper made, and the game lists with it, D-CLOUD-049). Each tier has a folder under one cloud root, and each folder is a pointer in `cloud_sync.conf`:

| Tier | Pointer | Default | Written by |
| --- | --- | --- | --- |
| saves | `SAVES_REMOTE` | `/ROCKNIX/Saves` | `cloud_backup`, `cloud_restore` |
| settings | `SETTINGS_REMOTE` | `/ROCKNIX/Backups` | `cloud_backup --system-only`, after `backuptool backup` |
| ROMs and BIOS, game content | `CONTENT_REMOTE` | `/ROCKNIX/Content`, with `ROMs/` and `BIOS/` under it (D-CLOUD-018) | `cloud_content_backup`, `cloud_content_restore` |

Source: `projects/ROCKNIX/packages/network/rclone/sources/cloud_sync.conf` and `cloud_sync.conf.defaults` (`cloud_sync_helper` appends a missing key from the defaults at boot, so an upgraded device gets a new key without losing its own values). Inside `Saves` the tree mirrors the device: game saves under their system, `savestates/` and `screenshots/` as their own folders. A cloud folder is a path under the provider's root, and on bucket stores (S3, B2) its first component is the bucket, which is why `cloud_setup` refuses a name the provider cannot use. A pointer is compared as a folder, never as a string, and one with `..` is refused (D-CLOUD-152).

The device's own name in the cloud is `cloud_device_id`: generated once, kept under `/storage/.config`, derived from a hardware address when there is one and random otherwise, and the stored value wins from then on, so a replaced Wi-Fi module does not strand the backups. It names the settings archive's folder.

## The allowlist

`cloud_sync-rules.txt` (defaults in `cloud_sync-rules.txt.defaults`, the player's own rules kept ahead of them) is an rclone filter file: `+` includes, `-` excludes, **first match wins**, and the last line is `- /**`. Anything not included is never touched. Databases and their sidecars are excluded before anything else can include them, because rclone replaces a file whole and a `.db` copied mid-write or separated from its `-wal` is a loss nobody can undo by hand. Then the three save folders and the save file types, and the standalone N64 saves that sit beside the ROMs.

## Which script runs when

Every cloud command the interface runs is a shell script under `/usr/bin`; EmulationStation never calls rclone itself.

| Moment | Command | Source |
| --- | --- | --- |
| a game exits | `cloud_capture --system S --rom R --emulator E --core C --started EPOCH --exit N`, then, with the toggle on, `cloud_backup --yes --saves-only --recent --automatic` | `es-app/src/FileData.cpp`, `ProxyCards.cpp` |
| startup, with the toggle on | `cloud_restore --yes --method=copy --update --saves-only --automatic`, then `cloud_backup --yes --method=copy --update --saves-only --automatic` | `es-app/src/main.cpp` |
| SYNC SAVES WITH THE CLOUD | the same pair, without `--automatic` | `guis/GuiMenu.cpp` |
| BACK UP SAVES / RESTORE SAVES | `cloud_backup --yes --saves-only` / `cloud_restore --yes --saves-only` | `guis/GuiMenu.cpp` |
| the transfer page | `cloud_backup` or `cloud_restore` with the ticked tiers; `cloud_content_backup`, `cloud_content_restore`, `cloud_content_restore --match` | `guis/GuiCloudTransfer.cpp` |
| boot | `cloud_capture --full`, detached and niced | `projects/ROCKNIX/packages/network/rclone/autostart/102-cloud-saves` |

A deliberate run (a row the player pressed) and an automatic one (startup, game exit) are two contracts, never one budget (D-CLOUD-113): the deliberate run may take as long as the files need and says so on its page; the automatic run is quick and waited for.

## The automatic sync's bounds

`cloud_backup` and `cloud_restore` run every rclone through one wrapper (`rclone()` in each script, at column 0 so the harness can lift it). On the automatic branch the whole run is under busybox `timeout` at `SYNC_CEILING_SECONDS` (default 90, `cloud_sync.conf.defaults`), and the wrapper watches rclone's progress through a fifo so a stall ends the run rather than the ceiling being spent on a transfer that is moving. A run the ceiling ends returns 124 and the card reads `COULDN'T FINISH - THE CLOUD TOOK TOO LONG`. The deliberate branch has its own stall ceiling, sized from rclone's idle timeout plus a grace (D-CLOUD-126).

`--recent` means only the saves newer than the last backup that worked (its stamp, minus a ten-minute margin so a save written while that run was still listing is inside the window; no stamp reads as "never"), copied with rclone's age filter, which skips listing the destination when few files qualify, so an exit with nothing changed never touches the remote. It is time, not the game's name: standalone emulators keep saves under their own layouts. And it always copies, never syncs, since a filtered sync would weigh deleting whatever the filter hid; the full passes (startup, the rows) catch a save with a wrong mtime. The starting budget for that run is 3 s for one changed battery save on a hashed cloud (D-CLOUD-119; measured 0.8 s), and `tools/time-to-play` fails a run over it (D-CLOUD-098).

A launch never cancels a sync the player can see. It waits, bounded (D-CLOUD-109); while a game runs, a sync that would have started is skipped with `SKIPPED - A GAME WAS STARTED`. Two exit codes are sentinels rclone cannot return: 69 (no network) and 75 (the transfer lock held), which the cards read as `SKIPPED - YOU'RE NOT ONLINE` and `SKIPPED - A SYNC IS ALREADY RUNNING`. Every other failure is `COULDN'T FINISH - <why>`, the why printed by the script on a `>>> why` line at the point of failure and carried in the stamp as one token (`es-player-text.md` § Outcome vocabulary).

The transfer lock is `/var/run/cloud_sync.lock`, an `flock` (the file stays behind after every run; only `flock -n` tells you whether it is held). Every writer of the saves tree inside EmulationStation is gated by it, the save-state manager included (D-CLOUD-053).

## Remotes that compare by size alone

rclone judges whether a file changed by size and modtime, or by hash where the backend has one. A plain WebDAV server (any vendor but Nextcloud, ownCloud, SharePoint and rclone's own `serve`) keeps neither a modtime rclone trusts nor a hash, so it compares by size, and a battery save, which is the same size every time it is written, never moved again after its first upload while the cards said COMPLETED (#315). Every saves pass, both scripts, both directions, the exit sync's recent set included, now runs with `--update` on such a remote: the local mtime against the backend's upload time (D-CLOUD-153, refined by D-CLOUD-154 to `--update` alone, no `--ignore-times`, no `--modify-window`).

Two consequences, both measured with the image's rclone 1.75.1 (D-CLOUD-155): the backend keeps its upload time in whole seconds, so a same-size change written in the same second as its upload is not sent until the next write (the tests wait two seconds past it); and a save written while the device's clock was wrong is not sent. After this update the first startup can bring back the cloud's older copy of such a save; the replaced copy is set aside for one cycle (below). Nothing changes on Dropbox, Google Drive, OneDrive, Nextcloud, S3, SFTP or SMB.

## The save manifest, the stage and the capture

`cloud_capture` records what a game session wrote, in this device's manifest under `/storage/.cache/cloud_sync/manifest-<device id>.json` (schema: `docs/save-manifest-schema.md`, rev 2, D-CLOUD-045). A save version is the sha256 of its bytes, explained by who wrote it: which device, which emulator and core, which build of that core. Only the exit path knows the last three, so EmulationStation calls it after every game whether or not the cloud toggles are on and whether or not the emulator exited cleanly. The hash is taken from an independent copy under `/storage/.cache/cloud_sync/stage/<sha256>`, never from the live file and never through a hard link, because a link follows the next in-place flush and then the bytes the transfer pushes are not the bytes the hash describes (D-CLOUD-034). A state's thumbnail is a declared member without an entry of its own (D-CLOUD-059).

Modes, exactly one per run: `--exit` (the session's unit), `--rescan` (after the save-state manager renumbered), `--full` (the boot pass: re-hash every path the manifest already claims, adopt nothing), `--retire PATH` (a deliberate deletion, written as a retired row before the file goes), `--retire --unlink` (the row, then the files, in one process that ignores SIGTERM, D-CLOUD-133), `--adopt` (a copy the manager made). Exit codes: 0 recorded or nothing to record; 1 could not record; 2 usage; 3 the copy was not a state of this unit.

Two writers can overlap (the detached boot pass and the first game's exit). Each loads the manifest, and whichever commits second sees the inode or mtime moved and discards its own document; an exit, rescan, retire or adopt re-runs itself once against the winner's. The commit itself (the check, the rename, the stage's garbage collection, the stamp) runs under `/storage/.cache/cloud_sync/.capture.lock`. An exit capture that has run past 100 s commits nothing, so a launch the gate released cannot have its saves recorded by the capture it left behind (D-CLOUD-151).

Every run leaves a line in `/storage/.cache/cloud_sync/last-capture`, one line per mode, each replaced only by a run of the same mode (D-CLOUD-070), and a run that could not record adds one to `capture-failures`. That is how "did any exit go unrecorded on this device?" is answered after a reboot, since `/var/log` is tmpfs.

## What a transfer replaces is kept for one cycle

The saves restore passes `--backup-dir /storage/.cache/cloud_sync/replaced/<stamp>`, so a local save the cloud copy overwrites is moved aside rather than lost; the saves backup passes `--backup-dir <SAVES_REMOTE>-replaced/<stamp>` on the cloud side. After a run that completed, every stamp folder but the newest is removed on that side, the remote's only on a full pass, so one record is at rest (D-CLOUD-078). The `-replaced` folder on the cloud is shared by every device on the saves folder. rclone's `<name>.<8 chars>.partial` litter is removed after each saves transfer.

## The stamps, markers and locks

The dotfiles and the `.cache` tree a reader meets on a device, and who writes each:

| Path | What | Writer |
| --- | --- | --- |
| `/storage/.cache/cloud_sync/last-backup`, `last-restore`, `last-settings-backup`, `last-settings-restore`, `last-content-backup`, `last-content-restore`, `last-content-match` | one line per deliberate operation: `<epoch> <rc> [<WHY_AS_ONE_TOKEN>]`; the rows read them (uncached, since ES caches `exists`) | the scripts |
| `/storage/.cache/cloud_sync/last-sync-startup`, `last-sync-exit`, `last-sync-link` | the automatic runs' stamps: the startup sync, the exit sync, the sync at the link's return | EmulationStation's cards (`ProxyCards.cpp`) |
| `/storage/.cache/cloud_sync/last-capture`, `capture-failures` | above | `cloud_capture` |
| `/storage/.cache/cloud_sync/manifest-<id>.json`, `stage/`, `.capture.lock` | above | `cloud_capture` |
| `/storage/.cache/cloud_sync/replaced/<stamp>/` | the set-aside | `cloud_restore` |
| `/storage/.cache/cloud_sync/content-match-plan` | the per-system plan the match preview wrote; `--match --apply` reads it and uses it up, and refuses a system missing from it or whose count grew (D-CLOUD-141) | `cloud_content_restore` |
| `/storage/.cache/cloud_sync/content-systems` | what the transfer page's tick page and the systems page chose, read back before a run continues | `GuiMenu.cpp` |
| `/storage/.config/.restore-finish-pending` | written by `backuptool restore`; while it exists FINISH RESTORE PROCESS appears under CLOUD STORAGE SETUP and the wizard opens at boot | `backuptool` |
| `/var/run/cloud_sync.lock` | the transfer lock (`flock`) | every transfer |
| `/var/log/cloud_sync.log` | the scripts' log; tmpfs, gone at reboot; passwords masked (D-SYS-013) | the scripts |

## The settings archive, and the last good settings

`backuptool backup` writes `<stamp>-<device>-ROCKNIX_SETTINGS.tar.gz` into the settings backups folder from a list of locations under `/storage` (`backuptool.conf` is read as text, never sourced, D-CLOUD-142); `cloud_backup --system-only` then uploads that folder to the device's folder under `SETTINGS_REMOTE`. With `STRIP=1`, the default, every `.key`, `.password` and `.token` line and every credential-shaped file is held back, and a backup that still finds a sign-in is refused before the archive exists (D-CLOUD-144; D-RA-025). The archive is written whole to a temporary name and renamed, and rotation runs after. A restore keeps a way back and, if it is cut short, is undone at the next boot; the marker above then asks for the credentials the archive could not carry, Wi-Fi first.

`system.cfg` has a last known good copy, `system.cfg.backup`, written by `chksysconfig` only from a file that has just been checked (at boot once verify has run, and at shutdown), to a temporary name and renamed (D-CLOUD-078). Verify tries the live file, then the record, then the image defaults, and says in the journal which one it took. A cut `system.cfg` is never completed by a shell writer or recorded as whole (D-SYS-011). The settings lock on both sides of the file is born with its holder's pid, and the interface keeps a change it could not take the lock for within five seconds (D-CLOUD-145).

## ROMs and BIOS, and the match

`cloud_content_backup` and `cloud_content_restore` copy a system's folder at a time under `CONTENT_REMOTE/ROMs/<system>` and `BIOS/`; both are copy-only and never delete. `cloud_content_restore --match` is the one action in these menus that deletes: it makes the device's `ROMs/` and `BIOS/` mirror the cloud, shows the per-system plan first, and `--apply` is held to that plan (D-CLOUD-023, D-CLOUD-141). The layout migration behind TIDY UP YOUR CLOUD FOLDERS (`cloud_migrate_layout`) moves the backups first and never inside Saves, resumes each tier against its own source, and deletes only the files it copied and checked (D-CLOUD-143).

## Offline achievements

**The service.** `raofflineproxy` packages RAOfflineProxy (`projects/ROCKNIX/packages/network/raofflineproxy`, pinned by commit) as a Python module in the image's site-packages, run by `raofflineproxy.service` as `python3 -m raofflineproxy.main run-service`, with its state under `/storage/.config/raofflineproxy` (`RAOFFLINEPROXY_CONFIG_DIR`). The unit is gated on `/storage/.cache/services/raofflineproxy.conf` like sshd's, and counts as started only once the proxy is listening (`ExecStartPost=raofflineproxy-ctl listening --wait 30`, D-RA-040). It listens on `127.0.0.1:8080`, and `setsettings.sh` points RetroArch at it at every launch (`cheevos_custom_host`) while the toggle is on; PPSSPP is pointed at it by `cheevos_ppsspp.sh` (under `ppsspp-sa/scripts`, its `AchievementsHost`), routed only when hardcore reads as off. The OS owns the launch-time configuration, so none of upstream's config patchers, menu or boot hook ships (D-RA-001).

**What it holds.** Its SQLite store keeps the cached achievement sets, the player's unlocks, the cached sign-in of the configured account (patch 007) and the casual awards earned without a connection; `cached_game_ids.txt` lists the cached games; `online_state.json`, `running`, `last-scan` and `last-flush` are the stamps the interface reads. The proxy is casual-only: RetroAchievements itself prepends a "Warning: Casual Only" achievement for a client it allows only casual unlocks from, and the toggle's own explanation carries that message (D-RA-003, D-RA-005). Turning the toggle on turns hardcore off, with the sentence on screen, never silently (D-RA-002).

**The control script.** `raofflineproxy-ctl` is the toggle's backend: `enable` (write the marker, start the service, record hardcore as it was, turn it off, set the toggle last, each write read back, and a step that fails undoes the ones before it), `disable` (the reverse, and hardcore put back as the record says), `start`, `stop`, `status`, `listening`, `scan`, `pending` (how many casual awards are waiting; exit 2 and no count when the store cannot be read, so nothing is promised on a guess), and `flushed` (the stamp the service leaves after a flush that sent awards, printed once and removed, so two readers cannot report the same one). EmulationStation asks `pending` as the exit sync card ends and `flushed` as the next sync card that reached the network ends (D-RA-004).

**The scan and the top-up.** SCAN GAMES FOR OFFLINE ACHIEVEMENTS runs `raofflineproxy-ctl scan`, which writes a job list and runs `raofflineproxy-cache-indexed`: a game the interface's own index already identified (a `cheevosId` and a hash) is cached from those without reading the ROM; a game the index does not know is hashed by the client's own path (D-RA-013). `raofflineproxy-cache-images` fetches the badges of every cached set, since to a player caching a game and caching its images are one action (D-RA-027). INDEX NEW GAMES AT STARTUP feeds the same cache as the hasher finishes, so turning the toggle on turns that index on. At the link's return the top-up asks one question, was a game played since the last attempt, and runs only over the games played (D-RA-035); the hash library's fetch that the index starts with ends after thirty seconds without a byte, so an index started offline never holds the interface (D-RA-036). The service re-reads, each online hour while idle, every cached game played in the last seven days; `raofflineproxy-refresh` does the same on request (D-RA-029).

**The cards.** `es-app/src/ProxyCards.cpp` owns them: the send card (`RETROACHIEVEMENTS`: `SENDING N EARNED OFFLINE...`, then `WHAT YOU EARNED OFFLINE IS NOW ON YOUR ACCOUNT.` or `COULDN'T FINISH - ...` with `IT'LL TRY AGAIN WHEN YOU'RE CONNECTED.`), the top-up card (`RETROACHIEVEMENTS (OFFLINE)`: `GETTING GAME 2 OF 5 READY...`, then `N MORE GAMES ARE READY.` or `EVERYTHING'S UP TO DATE.`), and the game-list card that says `NEWLY ADDED GAMES WILL BE ENABLED ONCE YOU RECONNECT.` They ride the surfaces that already run, the exit sync and the startup sync, with no separate connectivity monitor (D-RA-004, D-RA-017). At the link's return the achievements' cards come together and the saves sync after them.

**The patches.** Fifteen, under the package's `patches/` (numbered to 016; 006 was dropped), each named for what it does: a 4xx from upstream passed through rather than masked (001), no synthetic casual-only achievement from the proxy itself (002), the flush stamp (003), no cap on cached games (004), the refresh thread kept alive after a failed pass (005), the cached sign-in of the configured account (007), log upload opt-in (008), unique image temp names (009), a store-only request header the interface uses for offline lookups (010, 012), an offline login header (011), a cached image validated before it is published (013), one connection per thread for images (014), a bounded name lookup (015), and a download that says what became of it (016). What the fork changes goes back upstream as PRs and findings (D-RA-016).

## The save-state manager's bookkeeping

The manager (`es-app/src/guis/GuiSaveState.cpp`) is a writer of the saves tree like any transfer, so it is gated by the transfer lock, and every deletion it makes is recorded before the file goes (D-CLOUD-053): it runs `cloud_capture --retire --unlink` with the paths, one process, the retired row then the files, SIGTERM ignored, and removes only what the script left behind (D-CLOUD-133). A renumbering is followed by `cloud_capture --rescan` so moved versions keep their identity; a copy it makes is `--adopt`ed as the source's version at the new path. Thumbnails are members, not entries (D-CLOUD-059). The reconciler can therefore tell "deleted on purpose" from "never arrived".

## Wi-Fi

`wifictl` (`projects/ROCKNIX/packages/rocknix/sources/scripts/wifictl`) fronts NetworkManager with the iwd backend. The interface's rows read it rather than the `wifi.ssid` setting: `current` (the network joined now; exit 1 when none, 2 when NetworkManager could not be asked), `saved` and `saved --ssid` (the remembered profiles, one per line, `<name><TAB>[<ssid><TAB>]active|saved`), `join <name>` (a saved network with the key NetworkManager holds; prints `joined`), `forget <name>` (prints `forgotten`, then `disconnected` when it was the one in use), and `connect` (a new network: the saved profile is brought up as it is when there is one, else the key is stored in the profile with `psk-flags 0`). Exit codes: 0, 1 (not a saved network, or the operation failed; nothing printed), 2 (NetworkManager not answering).

The picker (`es-app/src/guis/GuiWifi.cpp`, its pure rules in `WifiText.cpp` with unit tests) decides what a press does from the row: connected, join again; saved, ask `CONNECT WITH ITS SAVED KEY, OR FORGET IT?`; the saved list unreadable, offer to check again; otherwise ask for the key. FORGET is the same confirmation and outcome as MANAGE SAVED NETWORKS' (D-UI-118). A key is typed where the network is named, on the picker or on the restore wizard's WI-FI PASSWORD page, and NETWORK SETTINGS has no key row. The keyless fall-through in `connect_wifi` is #318's open lead.
