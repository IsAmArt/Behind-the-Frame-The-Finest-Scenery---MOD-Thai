# Back up, update, uninstall and roll back

[Home](../README_EN.md) · [ภาษาไทย](BACKUP_UNINSTALL_TH.md) · [Install](INSTALL_EN.md)

## 1. Back up the old mod

1. Close the game. Find the executable folder using the installation guide.
2. Create a backup folder **outside the game**, for example `Documents/BehindTheFrameThai_Backup/old-version/`. Never keep backup plugin DLLs in `BepInEx/plugins`.
3. Use File Explorer **Copy** and **Paste** for these items, retaining their relative folders:

```text
BepInEx/plugins/BehindTheFrameThai.Diagnostics.dll
BepInEx/plugins/tamolly_font.bundle
BepInEx/plugins/BehindTheFrameThai/                 ← all translation and artwork
BepInEx/config/dev.modthai.behindtheframe.diagnostics.cfg
```

4. Keep **DLL + Font Bundle + Localization/Artwork + Config together**, with the previous ZIP, version and checksums. Do not move/delete saves to make this backup.
5. If other mods or a loader already exist, back up their original loader/config separately before changing versions; the Thai mod's ownership list does not grant permission to remove shared files.

## 2. Update

With the game closed and backup complete, extract the new ZIP outside the game. Check [FILE_OWNERSHIP.json](../release/FILE_OWNERSHIP.json), then merge the mod's BepInEx folder into the same executable folder. Replace only this mod's intended files. Keep one plugin version, preserve other mods and back up a personalized mod config before retaining its settings. Do not guess a mixture of DLL, CSV and images from different releases.

## 3. Remove only the Thai mod

1. If menus work, choose **Settings → Language → English**, then close the game. If menus do not work, stop and ask for help; do not edit save text.
2. Open the **installed version's FILE_OWNERSHIP.json** with Notepad or a browser. `relative_install_path` means a file path relative to the actual executable folder, not a command to run.
3. In File Explorer, create a holding folder outside the game, such as `BehindTheFrameThai_Removed`. Move only confirmed files matching this mod's list there first. Back up changed/uncertain files and ask before removing them.
4. The main items are its DLL, bundle, translation/artwork under BehindTheFrameThai and its mod config shown above. Do not move unrelated files that happen to share a folder.
5. **Never delete the entire BepInEx/plugins folder**, shared BepInEx, winhttp.dll or another mod's settings. Removing the loader is a separate task requiring verified file ownership.
6. **Do not delete, move, edit or restore saves/Steam Cloud.** No New Game is necessary.

## 4. Roll back

Close the game, move only the new mod's files out using its ownership list, then copy back the **complete matching old DLL + bundle + data + config**. Keep one plugin version. If language, chapter availability or progress changes unexpectedly, stop and report it; do not reset/restore saves to force a comparison. Removing or rolling back this mod is not a promised fix for the black-screen or ESC issues.
