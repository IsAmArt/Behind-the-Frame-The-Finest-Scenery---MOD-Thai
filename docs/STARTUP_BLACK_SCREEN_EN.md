# Startup black screen — initial checks and recovery

[Home](../README_EN.md) · [ภาษาไทย](STARTUP_BLACK_SCREEN_TH.md) · [Uninstall/vanilla recovery](BACKUP_UNINSTALL_EN.md) · [Known Issues](../KNOWN_ISSUES.md)

## Three separate symptoms — owner evidence31October2026

**A: Black at startup before the menu.** Steam vanilla recovered after owner Registry edits (responsible value unknown). Epic vanilla recovered after backing up/renaming old LocalLow game data. These were different operations, not a default combined reset.

**B: Black on consecutive same-chapter re-entry.** Appears after the chapter title when gameplay should appear; audio/input may continue. Neither Registry nor LocalLow recovery is proven to fixB.

**C: Cutscenes not playing.** The publisher suggested H.264→VP8 for affected cases; [codec guidance](TROUBLESHOOTING_EN.md#video-codec) does not establish a fix forA/B.

**Basic runtime testing succeeded on both Steam and Epic Games Store on Windows x64, confirmed by the project owner on31October2026.** Vanilla, BepInEx and Thai selection/use passed, not all chapters/builds or identical binaries. If the game already works, **do not reset Registry/rename LocalLow just to install the mod**.

## Before the Registry

Stop mod installation. Check the original game from your intended store without BepInEx/the mod; existing users must use [ownership-verified vanilla recovery](BACKUP_UNINSTALL_EN.md). Confirm the intended game/EXE/store. If necessary, use Steam Verify after removing verified mod components; it does not necessarily remove all third-party additions. Retain errors/logs/timing. Do not delete saves or change Cloud. If the menu already works, **do not reset the Registry**; continue the normal vanilla→BepInEx→mod sequence.

## PlayerPrefs and save files are different locations

Unity's Windows PlayerPrefs uses a company/product Registry key. Persistent files, including the Save files historically inspected for this game, are under LocalLow:

```text
Registry: HKEY_CURRENT_USER\Software\Silver Lining Studio\Behind the Frame
Persistent files/Save: %USERPROFILE%\AppData\LocalLow\Silver Lining Studio\Behind the Frame
```

Do not automatically delete/overwrite Save/Steam Cloud. Only the optional backed-up Epic folder isolation below involves a manual data-folder rename, with its consequences explicitly accepted by the user. Exporting this key is **not** a backup of all save files. Every value's meaning is not confirmed; resetting the key could affect other state as well as preferences. [Unity PlayerPrefs](https://docs.unity3d.com/2019.4/Documentation/ScriptReference/PlayerPrefs.html) · [Unity Windows persistentDataPath](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Application-persistentDataPath.html) (the2022.3 page clarifies LocalLow, not the game's engine version).

## Optional Epic path used by the owner — back up and isolate old data

Only for vanilla startup failures after ordinary checks, not every installation or a default combined Registry+LocalLow reset. Steam may also be affected if stores share Company/Product/data paths; identical data/binaries are not assumed for every build.

1. Close game/launcher completely. Existing mod users need a vanilla recovery plan first; do not change data while adding mods.
2. **Win+R**, paste the **parent directory**, pressEnter:

```text
%USERPROFILE%\AppData\LocalLow\Silver Lining Studio
```

3. Confirm the child **Behind the Frame** at `%USERPROFILE%\AppData\LocalLow\Silver Lining Studio\Behind the Frame`. If missing/uncertain, stop; do not create/substitute a folder.
4. Right-click that child → **Copy**, thenPaste to a separate dated backup outside the game and original LocalLow folder, such asDocuments. Confirm the actual copy/files exist before renaming; a shortcut is not a backup.
5. Back in the parent, **Rename only Behind the Frame** to a unique name such as `Behind the Frame.before_test_YYYYMMDD`, never overwriting old backups. **Do not rename/delete the Silver Lining Studio parent**, and do not delete the old folder.
6. Launch Epic vanilla yourself once and test the menu. A fresh folder may be created; **saves/settings/unlocked chapters may temporarily disappear from view** while using it. This does not prove the original save was deleted. Keep old data/backups; do not force a NewGame/overwrite to pass.
7. If Cloud Sync restores old data or shows a conflict, **stop and review synchronization**; do not guess which Cloud/local copy to overwrite, merge folders or immediately restore saves. For rollback, close game/launcher and obtain a plan preserving old and new data first.

The owner confirmed Epic vanilla then BepInEx/Thai basic use after renaming old data; the responsible file and universal success remain unknown. This does not establish a fix for same-chapter symptomB or cutscene symptomC.

## Export only the game key first — Windows10/11

1. Close the game and all launchers, including Steam/Epic.
2. Press **Win+R**, type **regedit**, pressEnter; confirm the genuine Registry Editor prompt if shown.
3. Paste this into its address bar:

```text
HKEY_CURRENT_USER\Software\Silver Lining Studio\Behind the Frame
```

4. Confirm the selected **Behind the Frame** key under HKEY_CURRENT_USER → Software → Silver Lining Studio. If missing/uncertain, stop; do not create or substitute keys.
5. Right-click that key → **Export** (or File → Export).
6. Confirm **Selected branch** is exactly that game path, notAll; save a dated.reg **outside the game**.
7. Confirm the export exists. Inspect with Notepad if needed; do not double-click toImport. It is a pre-change snapshot, not a guaranteed good configuration.

Export guidance: [Microsoft](https://support.microsoft.com/en-us/windows/experience/backup-recovery/how-to-back-up-and-restore-the-registry-in-windows). Microsoft does not certify the game-specific reset below as a fix.

## Optional Steam path used by the owner — last-resort reset of the exported key only

Only after ordinary checks fail and you accept losing game preferences. Not routine installation advice and not guaranteed on every PC. Ask for help if unsure.

1. Keep game/launchers closed; recheck the exact selected path and exported file.
2. Right-click **only Behind the Frame** at the full path above → **Delete**. Read the key name before confirming; cancel if different. **Never delete Silver Lining Studio, Software or HKEY_CURRENT_USER**, or guess individual value changes.
3. Close Registry Editor. Launch Steam vanilla yourself once to allow new settings, record menu/black-screen result. Do not add BepInEx/the mod during this check.
4. If still black, stop and report. Do not repeatedly delete keys, restore saves/Cloud or attribute Epic recovery to this Registry edit; the owner used LocalLow isolation forEpic.

**Do not immediately Import the old backup**: if it contained the problem settings, restoring them may restore the problem. Keep it for comparison/considered rollback, using only your own Windows-account/machine backup. **Never import TA Font's or another player's Registry export.** No automatic deletion.reg/.bat is supplied. There is no evidence this fixes symptomB.

Once Steam or Epic vanilla reaches the menu, close it before [BepInEx first launch→wait for menu→close→Thai mod](INSTALL_EN.md). Do not reset preferences/data again just to install. The latest owner results are basic QA, not exhaustive chapter/build testing.

Sources: [Microsoft Registry export/import](https://support.microsoft.com/en-us/windows/experience/backup-recovery/how-to-back-up-and-restore-the-registry-in-windows) · [Unity2019.4 PlayerPrefs](https://docs.unity3d.com/2019.4/Documentation/ScriptReference/PlayerPrefs.html) · [Unity persistentDataPath](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Application-persistentDataPath.html) · [Steam Verify](https://help.steampowered.com/en/faqs/view/0C48-FCBD-DA71-93EB/)
