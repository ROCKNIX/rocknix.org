# :fontawesome-solid-medal: Retro Achievements

ROCKNIX has a native integration with [RetroAchievements](https://retroachievements.org/) which allows you to earn achievements as you play games across numerous emulators. In order to use RetroAchievements your device must be connected to the internet, unless you set up offline achievements (below).

## Setup

1. Create an account at [RetroAchievements.org](https://retroachievements.org/).
2. Follow the steps on the [Networking](../../configure/networking) page to connect your device to the internet.
3. While in EmulationStation press ++"START"++ on your controller to open the Main Menu.
4. Select `Game Settings` and then choose `RetroAchievement Settings`.
5. Turn On RetroAchievements (first toggle).
6. Then enter your username and password for RetroAchievements.org in the username and password fields.

<details> <summary>Screenshot: RetroAchievement Settings</summary>
  <img src="../../_inc/images/retro-achievements/retroachievements-settings.png" />
</details>

## Offline Achievements (Beta)

Achievements normally need a connection while you play. With offline achievements on, ROCKNIX keeps a copy of each game's achievement data on the device, records what you earn while you're offline, and sends it to your account the next time you're connected.

1. Under `RetroAchievement Settings`, select `Offline Achievements (Beta)` and turn it on. It works for casual achievements only, so hardcore mode goes off with it.
2. Select `Scan Games for Offline Achievements` while you're online. This looks at every game on the device and saves its achievement data; a large library takes a while, and the page stays open until it's done.

From then on you can play offline and earn achievements as usual. When the connection comes back, a card at the top of the screen reads `SENDING ... EARNED OFFLINE` and then `WHAT YOU EARNED OFFLINE IS NOW ON YOUR ACCOUNT`. If the send doesn't go through, it tries again the next time you're online; nothing is lost in between.

<details> <summary>Screenshot: the Offline Achievements page</summary>
  <img src="../../_inc/images/retro-achievements/offline-achievements.png" />
</details>

Games you add later are picked up by `Index New Games at Startup`, which turning on offline achievements switches on for you. A game added while you're offline can be played, but its achievements count once you've been online with it, and the startup card says so: `NEWLY ADDED GAMES WILL BE ENABLED ONCE YOU RECONNECT`.

## Additional Notes

- There are additional settings that can be changed in the above menu to tailor your experience.  Please see the documentation @ [docs.retroachievements.org](https://docs.retroachievements.org/) for details on each option
    - Recommended Settings:
    - Unlock Sound (++"On"++): this plays the classic unlock sound each time an achievement is earned.
    - Automatic Screenshot (++"On"++): this takes a screenshot each time an achievement is earned and stores it in the screenshots directory.  These can be viewed in the screenshots system in EmulationStation.
    - Progress Tracker (++"On"++): shows how far along you are toward an achievement while you play.
- If your build shows a `Web API Key` row under the password, enter the key from your account's settings page on RetroAchievements.org. The `RetroAchievements` page on the Main Menu uses it to show your progress.
- Not all emulators and games support RetroAchievements; please see the list of emulators that support achievements [here](https://docs.retroachievements.org/Emulator-Support-and-Issues/) and check if your game has achievements available by searching for it on RetroAchievements.org
- There is a change needed on the RetroAchievements API in order to be able to display to display your history of earned achievements in EmulationStation.  Once the needed change is made by RetroAchievements; we can look at renabling this functionality in EmulationStation.
