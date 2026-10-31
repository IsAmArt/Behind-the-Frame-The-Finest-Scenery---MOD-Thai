# Startup black screen — initial checks and recovery

[Home](../README_EN.md) · [ภาษาไทย](STARTUP_BLACK_SCREEN_TH.md) · [Uninstall/vanilla recovery](BACKUP_UNINSTALL_EN.md) · [Known Issues](../KNOWN_ISSUES.md)

## Two separate symptoms

**A: Black from startup, before the menu.** The owner encountered this in newly installed Steam without BepInEx/mods and in Epic vanilla. Steam now works after the owner changed game Registry settings. The responsible value/root cause is unknown; Epic has NOT been retested afterward. This is user-confirmed outcome, not a universal fix or proof of mod/native blame.

**B: Black after consecutive same-chapter entry.** The chapter-number screen may display, then gameplay imagery goes black while audio/input may continue. This remains a separate Known Issue. **Registry reset has not been shown to fix B.** Epic remains NOT VALIDATED/not supported for this mod.

## Before the Registry

Stop mod installation. Check the original Steam game without BepInEx/the mod; existing users must use [ownership-verified vanilla recovery](BACKUP_UNINSTALL_EN.md). Confirm the intended game/EXE/store. If necessary, use Steam Verify after removing verified mod components; it does not necessarily remove all third-party additions. Retain errors/logs/timing. Do not delete saves or change Cloud. If the menu already works, **do not reset the Registry**; continue the normal vanilla→BepInEx→mod sequence.

## PlayerPrefs and save files are different locations

Unity's Windows PlayerPrefs uses a company/product Registry key. Persistent files, including the Save files historically inspected for this game, are under LocalLow:

```text
Registry: HKEY_CURRENT_USER\Software\Silver Lining Studio\Behind the Frame
Persistent files/Save: %USERPROFILE%AppDataLocalLowSilver Lining StudioBehind the Frame
```

Do not delete/move/reset Save/Steam Cloud. Exporting this key is **not** a backup of all save files. Every value's meaning is not confirmed; resetting the key could affect other state as well as preferences. [Unity PlayerPrefs](https://docs.unity3d.com/2019.4/Documentation/ScriptReference/PlayerPrefs.html) · [Unity Windows persistentDataPath](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Application-persistentDataPath.html) (the2022.3 page clarifies LocalLow, not the game's engine version).

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

## Last-resort manual reset of that exported key only

Only after ordinary checks fail and you accept losing game preferences. Not routine installation advice and not guaranteed on every PC. Ask for help if unsure.

1. Keep game/launchers closed; recheck the exact selected path and exported file.
2. Right-click **only Behind the Frame** at the full path above → **Delete**. Read the key name before confirming; cancel if different. **Never delete Silver Lining Studio, Software or HKEY_CURRENT_USER**, or guess individual value changes.
3. Close Registry Editor. Launch Steam vanilla yourself once to allow new settings, record menu/black-screen result. Do not add BepInEx/the mod during this check.
4. If still black, stop and report. Do not repeatedly delete keys, restore saves/Cloud or infer that Epic is fixed.

**Do not immediately Import the old backup**: if it contained the problem settings, restoring them may restore the problem. Keep it for comparison/considered rollback, using only your own Windows-account/machine backup. **Never import TA Font's or another player's Registry export.** No automatic deletion.reg/.bat is supplied. There is no evidence this fixes symptomB.

Once Steam vanilla reaches the menu, close it before [installing/checking BepInEx separately, then the Thai mod](INSTALL_EN.md). Do not reset preferences again just to install. Epic after the Registry change remains untested.

Sources: [Microsoft Registry export/import](https://support.microsoft.com/en-us/windows/experience/backup-recovery/how-to-back-up-and-restore-the-registry-in-windows) · [Unity2019.4 PlayerPrefs](https://docs.unity3d.com/2019.4/Documentation/ScriptReference/PlayerPrefs.html) · [Unity persistentDataPath](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Application-persistentDataPath.html) · [Steam Verify](https://help.steampowered.com/en/faqs/view/0C48-FCBD-DA71-93EB/)
