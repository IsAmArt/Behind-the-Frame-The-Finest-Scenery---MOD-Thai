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
2. Back up the current matching DLL + bundle + translation/artwork + config first, using section1.
3. Open the **installed version's FILE_OWNERSHIP.json** with Notepad or a browser. `relative_install_path` means a file path relative to the actual executable folder, not a command to run.
4. In File Explorer, create a holding folder outside the game, such as `BehindTheFrameThai_Removed`. Move only confirmed files matching this mod's list there first. Back up changed/uncertain files and ask before removing them.
5. The main items are its DLL, bundle, translation/artwork under BehindTheFrameThai and its mod config shown above. Do not move unrelated files that happen to share a folder.
6. **Never delete the entire BepInEx/plugins folder**, shared BepInEx, winhttp.dll or another mod's settings. Removing the loader is a separate task requiring verified file ownership.
7. **Do not delete, move, edit or restore saves/Steam Cloud.** No New Game is necessary.

8. Launch the game yourself to check the result. Stop on unexpected behavior; do not restore saves by guesswork.

## 4. Roll back

Close the game, move only the new mod's files out using its ownership list, then copy back the **complete matching old DLL + bundle + data + config**. Keep one plugin version. If language, chapter availability or progress changes unexpectedly, stop and report it; do not reset/restore saves to force a comparison. Removing or rolling back this mod is not a promised fix for the black-screen or ESC issues.


## 5. Vanilla without BepInEx — only with verified file ownership

If other mods exist or loader ownership is unclear, **stop; do not move shared BepInEx**. Removing only the Thai plugin in section3 leaves the loader installed and is not a loader-free vanilla test.

1. Select English if menus work, then close the game and all launchers. Keep the complete current mod and pre-install backups outside the game.
2. Compare your installation records, exact BepInEx ZIP and pre-install backup. Confirm each component was added **only for this mod**, not an original game file, another mod or another application's.NET installation. Ask if uncertain.
3. Pinned be.788 root entries are `winhttp.dll`, `doorstop_config.ini`, `.doorstop_version`, `changelog.txt`, `BepInEx/`, `dotnet/`. This is a reference, **not a blanket move/delete list**; names such as changelog.txt may belong to something else. Generated cache/interop/logs under BepInEx remain inside that folder.
4. In File Explorer, create a holding folder **outside the game**, copy backups first, then move only entries independently confirmed to belong to that BepInEx installation, including its verified root **winhttp.dll** loader. If an earlier file was overwritten during installation, stop and ask for an original-file recovery plan instead of assuming every named item can be moved. No automatic removal script is supplied.
5. Check for other loader routes or launch options you previously added; stop if unsure rather than randomly changing them. No console alone is insufficient proof of vanilla; also check for no new loader startup log. Preserve old logs.
6. If needed, Steam → Library → right-click game → Properties… → Installed Files → **Verify integrity of game files**, after verified mod components have been removed. Verify can repair missing/changed game files but **does not necessarily remove all added third-party files**; it does not replace checking the loader route.
7. Launch the game yourself and check the menu. If still black at startup, use [startup checks](STARTUP_BLACK_SCREEN_EN.md), not automatic Save/Cloud/Registry changes. Loader-free vanilla is not a guaranteed fix for same-chapter re-entry black screens.

Do not move the game EXE, GameAssembly.dll, UnityPlayer.dll, `_Data`, Save/LocalLow or Steam Cloud as BepInEx components. Registry reset is not an uninstall step.

[Steam: Verify Integrity](https://help.steampowered.com/en/faqs/view/0C48-FCBD-DA71-93EB/) · [BepInEx IL2CPP installation](https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html)
