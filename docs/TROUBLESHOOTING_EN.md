# Troubleshooting — questions and answers

[Home](../README_EN.md) · [ภาษาไทย](TROUBLESHOOTING_TH.md) · [Install](INSTALL_EN.md) · [Known Issues](../KNOWN_ISSUES.md)

## Where is the game folder?

Steam → Library → right-click the game → Properties… → Installed Files → Browse…. Find **Behind the Frame.exe**, possibly one level deeper in BehindTheFrame_PC_Steam. Stop if the executable is missing; do not create/guess a destination.

## I extracted a ZIP but cannot see the mod files

Make sure this is the Thai mod ZIP, not the separate BepInEx ZIP. Right-click → Extract All… → Extract; open the extracted package folder until README and BepInEx appear. If security software raises an alert, retain the filename/message and verify the ZIP with TA Font; do not disable protection or restore a quarantined file by guesswork.

## There is BepInEx/BepInEx nesting

Close the game and compare the installation tree. The plugin belongs at `BepInEx/plugins/BehindTheFrameThai.Diagnostics.dll` beside the executable, not under `BepInEx/BepInEx/plugins`. Back up the misplaced mod files outside the game, then copy only confirmed Thai-mod files to the correct paths using the ownership list. Preserve other mods; do not move/delete an entire shared folder blindly.

## The game launches but Thai is missing

Check the actual EXE folder, pinned IL2CPP-win-x64 be.788 loader, a single plugin version, tamolly_font.bundle and the CSV. First startup can take longer to generate files. Check Settings → Language. If Thai is still missing, preserve BepInEx/LogOutput.log and ErrorLog.log if present before restarting. Do not delete saves.

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
