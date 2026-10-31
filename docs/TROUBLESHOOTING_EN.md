# Troubleshooting — questions and answers

[Home](../README_EN.md) · [ภาษาไทย](TROUBLESHOOTING_TH.md) · [Install](INSTALL_EN.md) · [Known Issues](../KNOWN_ISSUES.md)

## Black screen from startup, before the menu?

This can occur even without BepInEx/the mod. Stop mod installation and read [Startup black screen — initial checks and recovery](STARTUP_BLACK_SCREEN_EN.md). The owner confirmed Steam working after Registry edits (responsible value unknown), and Epic working after backing up/renaming old LocalLow game data. Both stores passed basic Thai-mod use. This does not establish a fix for same-chapter re-entry black screens.

## Where is the game folder?

Steam → Library → Properties… → Installed Files → Browse…, or Epic → Library → … → Manage → install location. Find **Behind the Frame.exe**, possibly one level deeper in BehindTheFrame_PC_Steam. Stop if the executable is missing; do not create/guess a destination.

## I extracted a ZIP but cannot see the mod files

Make sure this is the Thai mod ZIP, not the separate BepInEx ZIP. Right-click → Extract All… → Extract; open the extracted package folder until README and BepInEx appear. If security software raises an alert, retain the filename/message and verify the ZIP with TA Font; do not disable protection or restore a quarantined file by guesswork.

## There is BepInEx/BepInEx nesting

Close the game and compare the installation tree. The plugin belongs at `BepInEx/plugins/BehindTheFrameThai.Diagnostics.dll` beside the executable, not under `BepInEx/BepInEx/plugins`. Back up the misplaced mod files outside the game, then copy only confirmed Thai-mod files to the correct paths using the ownership list. Preserve other mods; do not move/delete an entire shared folder blindly.

## The game launches but Thai is missing

Check the actual EXE folder, pinned IL2CPP-win-x64 be.788 loader, a single plugin version, tamolly_font.bundle and the CSV. First startup can take longer to generate files. Check Settings → Language. If Thai is still missing, preserve BepInEx/LogOutput.log and ErrorLog.log if present before restarting. Do not delete saves.

## BepInEx first launch — do not add the Thai mod yet

After copying official BepInEx contents beside **Behind the Frame.exe**:

1. **Do not copy the Thai mod yet.** Launch normally from the Steam or Epic Games Launcher installation you are using.
2. A separate black text window may appear: the **BepInEx console**. BepInEx is preparing/generating files required for Unity IL2CPP; **it is not installing the Thai mod**.
3. First launch may take longer. The owner saw yellow text before the game started, but console visibility/output/colors vary. **Yellow text is not a universal success condition.**
4. Do not close the console while initialization is actively progressing. Wait until the **actual game menu appears**, then close the game normally.
5. Only then extract/copy the Thai mod's BepInEx folder to the same EXE directory. Launch again → **Settings → Language → ไทย**.

If initialization errors/stops or the menu never appears, retain console errors/screenshots and available logs, such as BepInEx/LogOutput.log or .txt and ErrorLog.log, before retrying. Do not infer success from a color, disable security or reset data/Registry by guesswork. [Official IL2CPP instructions](https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html)

## Thai displays as squares or misplaced marks

Close the game and check that the DLL and font bundle are from the same complete package. Installing a Windows font is unnecessary. Keep the approved ThaiLegacyShaper/ThaiFontScaling settings; back up personalized settings before asking for help. Do not modify the TTF, re-save PNGs or mix releases.

## Can I overwrite an old release?

[Back up the whole mod first](BACKUP_UNINSTALL_EN.md). With the game closed, replace only the intended Thai-mod files. Keep one plugin version, no backup DLL in plugins, and preserve other mods. Back up your mod config before choosing new settings.

## The game stopped launching after BepInEx installation

Stop repeated attempts and retain any error/log. Check **6.0.0-be.788 Unity.IL2CPP-win-x64** and winhttp.dll beside the EXE; do not substitute Latest, Mono or x86. If you replaced an existing loader, ask for help with the file list and pre-install backup. Do not randomly delete loader/game files, reset saves, change Steam Cloud or disable security software.

## How do I return to English?

Select Settings → Language → English; uninstalling is optional. To remove the mod, follow [the uninstall guide](BACKUP_UNINSTALL_EN.md) after selecting English and closing the game. If menus are unavailable, ask for help instead of editing saveData.txt.

## Some artwork/Cinema is English

Existing fallback may select English when Thai images are missing/invalid. Check all34 notebook images and12 Cinema frames, exact names and original bytes. Do not re-save PNGs. Choose language before the sequence; switching during animation is untested.

## Re-entering the same chapter gives black imagery with audio

See [Known Issues](../KNOWN_ISSUES.md). The symptom is **after the chapter-number screen, when gameplay should appear**, distinct from normal black Loading/title backgrounds. Closing and reopening the game before entering again may help, without a guarantee. Do not force scene reloads, clear caches or delete saves. ESC flashing and Chapter6/Continue are separate issues; stop a failing Continue route and report it.

## What should I send TA Font?

Package/plugin versions, language, chapter/step, button route, visual/audio/input result and privacy-reviewed screenshots/logs. Preserve logs before another launch. Do not send saves, Cloud data or account identifiers unnecessarily. [Report a problem or rights-holder concern](https://github.com/IsAmArt/Behind-the-Frame-The-Finest-Scenery---MOD-Thai/issues).


## Extra information — cutscenes and Video Codec

### Video Codec

The publisher's **Behind the Frame Post-Launch Update**, dated **8July2022**, describes some cutscenes failing to trigger/play normally. It suggests switching **H.264 → VP8** in settings for affected configurations, specifically mentioning SteamDeck.

If you reach the menu but cutscenes malfunction, record the current setting, open **Settings → Video Codec** (some UI labels useVideo Format), select **VP8**, and test/record the result yourself. If it does not help, stop and retain evidence; do not force changes to game/data files.

This targets cutscene playback only. It is **not a confirmed fix for startup or consecutive same-chapter black screens**, or certification of this mod onSteamDeck.

[Original publisher announcement](https://steamcommunity.com/games/1634150/announcements/detail/3335495035148049868) · [Separate startup checks](STARTUP_BLACK_SCREEN_EN.md)
