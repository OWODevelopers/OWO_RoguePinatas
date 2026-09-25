# OWO_RoguePinatas
OWO integration for Rogue Piñatas: VRmageddon. This mod is a port of [Dteyn/RoguePinatas_bHaptics](https://github.com/Dteyn/RoguePinatas_bHaptics) (MIT): it keeps the original game hooks and replaces the bHaptics backend with OWO.

*Compatible with the Steam version of Rogue Piñatas: VRmageddon (build 19155164, game version 1.1.0) and BepInEx 5.4.23.2.*

> **Preview release.** The mod loads in the real game and has been tested with an OWO Skin, but some sensations have not been reviewed on hardware yet. Feedback is welcome in [Issues](../../issues).

## What is OWO?
OWO Skin is a haptic technology that lets you feel everything that happens in a video game.
OWO is capable of delivering highly realistic and precise sensations, such as the feeling of impact, the recoil of your weapons or even the subtle sensation of insects moving across your skin.

Want to get an OWO Suit? [Look here](https://owogame.com/shop/).

## Requirements
- Rogue Piñatas: VRmageddon (Steam, PC VR).
- [BepInEx 5.4.23.2](https://github.com/BepInEx/BepInEx/releases/tag/v5.4.23.2), Windows x64 build (`BepInEx_win_x64_5.4.23.2.zip`).
- MyOWO open on the same PC or on the same local network, with your OWO Skin connected and calibrated.

## Installation
1. **Install BepInEx.** Download `BepInEx_win_x64_5.4.23.2.zip` and extract it into the game folder, so that `BepInEx`, `winhttp.dll` and `doorstop_config.ini` end up next to the game's `.exe`.
   To find the game folder: in Steam, right-click the game → *Manage* → *Browse local files*.
2. **Run the game once** and close it. BepInEx creates its folders (`BepInEx\plugins`, `BepInEx\config`, …) on this first run.
3. **Download the mod** from [Releases](../../releases): `RoguePinatas_OWO_v1.0.4.zip` (the newest version at the top).
4. **Extract the mod zip into the game folder** (the same folder as in step 1) and accept merging the `BepInEx` folder. You should end up with:
   ```
   <game folder>\BepInEx\plugins\RoguePinatas_OWO\RoguePinatas_OWO.dll
   <game folder>\BepInEx\plugins\RoguePinatas_OWO\OWO.dll
   <game folder>\BepInEx\plugins\RoguePinatas_OWO\sensations\*.owo
   <game folder>\BepInEx\config\RoguePinatas_OWO.cfg
   ```
5. **Connect with MyOWO.** Open MyOWO and go to its games screen, then start the game. When **Rogue Piñatas VRmaggedon** appears in MyOWO's list, **click it**: MyOWO does not connect a game until you select it. A heartbeat on the left side of your chest confirms the connection.
6. Enjoy your immersive experience! 😊

### Check that it works
Open `<game folder>\BepInEx\LogOutput.log`. It should contain:
- `installed 21/21 hooks`
- `connection state: Connected` after you click the game in MyOWO

The warning `BepInEx manager object destroyed while the game is running…` is expected for this game; the mod keeps running on its own object.

## Featured effects
- Heartbeat (low health, and a single pulse when MyOWO connects)
- Impact (front/side, directional)
- Impact from behind
- Explosion (scaled by distance)
- Death
- Revive
- Heal
- Level up
- PartiBox
- Candy pickup
- Meta-candy pickup
- Weapon recoil (left hand, right hand, both hands)
- Melee hit (left, right)
- JolliZapper (left, right)
- BoomBoxer (left, right)

## Configuration
Edit `<game folder>\BepInEx\config\RoguePinatas_OWO.cfg` with the game closed:
- `Enabled=1`: set it to `0` to turn the mod off completely (no hooks are installed).
- `GameId`: the game's OWO id. Do not change it.
- `ServerIp=`: leave it empty for automatic connection (see *Manual connection*).
- `LogEnabled=0`: set it to `1` to write every haptic decision to `BepInEx\RoguePinatas_OWO.trace.log` (for bug reports).
- `[Intensity]`: `Default` scales every sensation (1.0 = designed strength; try `0.6` for gentler feedback). The other keys keep the names and defaults of the original bHaptics mod, plus one multiplier per sensation.

## Manual connection
If the game does not appear in MyOWO (VPN, or a network that blocks broadcast), write the IP address that MyOWO shows into `ServerIp=` in `BepInEx\config\RoguePinatas_OWO.cfg` (several IPs can be separated by commas) and restart the game. Do not use `127.0.0.1`.

## Uninstall
Delete `BepInEx\plugins\RoguePinatas_OWO\` and `BepInEx\config\RoguePinatas_OWO.cfg` from the game folder. To remove BepInEx as well, also delete `BepInEx\`, `winhttp.dll`, `doorstop_config.ini` and `.doorstop_version`, or verify the game files in Steam.

## Credits
- Original bHaptics mod and game hooks: [Dteyn](https://github.com/Dteyn/RoguePinatas_bHaptics), MIT License.
- OWO SDK (`OWO.dll`): OWO, MIT License.
- [BepInEx](https://github.com/BepInEx/BepInEx) and [Harmony](https://github.com/pardeike/Harmony).

The licence texts ship inside the release zip, in `BepInEx\plugins\RoguePinatas_OWO\licenses\` and `THIRD_PARTY_NOTICES.txt`.
