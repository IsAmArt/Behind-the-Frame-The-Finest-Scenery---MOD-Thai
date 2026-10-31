# Install the Thai mod — step by step

[Home](../README_EN.md) · [ภาษาไทย](INSTALL_TH.md) · [Troubleshooting](TROUBLESHOOTING_EN.md)

**Full Content — Public Pre-release.** Complete Thai content, incomplete exact-package gameplay QA and known issues. The user performs every game launch.

## 0. Check vanilla before adding anything

1. Install the Steam or Epic version you will use and reach its menu **without mods or BepInEx**. Existing mod users should first follow [safe vanilla recovery](BACKUP_UNINSTALL_EN.md).
2. If the menu works, close the game; then download/install the pinned BepInEx build.
3. Check BepInEx alone, then close the game before downloading/copying the Thai mod as described below.

If vanilla is black at startup, **do not install BepInEx/the mod yet**. Read [Startup black screen — initial checks and recovery](STARTUP_BLACK_SCREEN_EN.md). Registry reset is not a routine installation step and must not be repeated on every installation.

These are the latest online instructions; the v1.0.0-rc1 ZIP remains unchanged.

## 1. Before you start

You need the Steam or Epic Games Store game on Windows x64, the separate **BepInEx 6.0.0-be.788 Unity.IL2CPP-win-x64 ZIP**, the **Thai mod ZIP**, and Windows **Extract All…** or a ZIP-capable application. BepInEx and the Thai mod are **two different downloads**. The base game should already launch normally. No New Game, save reset or standalone font installation is required. Existing mod users should [back up first](BACKUP_UNINSTALL_EN.md).

## 2. Find the actual EXE folder — by launcher

### Steam

Library → right-click game → Properties… → Installed Files → Browse…. Find **Behind the Frame.exe**, possibly inside **BehindTheFrame_PC_Steam**.

```text
folder opened by Steam Browse/
└─ BehindTheFrame_PC_Steam/      ← if present, open it
   ├─ Behind the Frame.exe      ← place BepInEx beside this
   └─ Behind the Frame_Data/    ← not the mod destination
```

### Epic Games Store

Epic Games Launcher → Library → game **… → Manage**, then **Open Install Location** or its folder icon. If labels differ, read the installation location and open it in File Explorer. Find the **actual Behind the Frame.exe** belonging to that Epic installation, not a guessed Steam path.

```text
Epic game installation folder/
├─ .egstore/                    ← launcher metadata; not a mod destination
└─ actual EXE folder/           ← can be this folder itself or a subfolder
   ├─ Behind the Frame.exe      ← place BepInEx beside this
   └─ Behind the Frame_Data/    ← not a mod destination
```

These are schematics, not screenshots or proof every build has the same layout. If the EXE is in the outer folder, use that; do not create a new folder to match the diagram. Never install in Save, Behind the Frame_Data, .egstore or nested BepInEx/BepInEx. Stop if the EXE is missing.

[Publisher support: Steam/Epic folder options](https://support.microids.com/en/support/solutions/articles/23000007351-finding-the-executable-file-exe-of-your-pc-game)

## 3. Install BepInEx

1. Click **ดาวน์โหลด BepInEx 6.0.0-be.788** on the README or [download this exact official archive](https://builds.bepinex.dev/projects/bepinex_be/788/BepInEx-Unity.IL2CPP-win-x64-6.0.0-be.788%2B5b766a3.zip).
2. Open Downloads, right-click the ZIP → **Extract All… → Extract**. Windows11 may put commands under **Show more options**.
3. Open the extracted folder until you see **winhttp.dll**, **doorstop_config.ini**, **BepInEx** and **dotnet**.
4. Close the game. Select the archive's contents → right-click **Copy**. Open the folder containing **Behind the Frame.exe**, right-click an empty area → **Paste**. Do not copy the enclosing archive-name folder.
5. Confirm **winhttp.dll** and **BepInEx** sit beside the EXE.
6. After vanilla reaches its menu, launch through Steam or Epic Games Launcher to check BepInEx separately. Follow the first-launch section below and wait for the actual menu.
7. **Close the game before copying the Thai mod.**

If BepInEx or other mods already exist, back up and verify the loader version before replacing anything. Preserve the player's global `BepInEx/config/BepInEx.cfg`. Do not substitute Mono, x86, BepInEx5 or an arbitrary Latest build.

[Official IL2CPP instructions](https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html). Verified archive SHA-256: `F4CC496BD098A0DF4164B81E3737297707F13A47C2478DBA2F60EEFAB784817A`.

## BepInEx first launch — do not add the Thai mod yet

After copying official BepInEx contents beside **Behind the Frame.exe**:

1. **Do not copy the Thai mod yet.** Launch normally from the Steam or Epic Games Launcher installation you are using.
2. A separate black text window may appear: the **BepInEx console**. BepInEx is preparing/generating files required for Unity IL2CPP; **it is not installing the Thai mod**.
3. First launch may take longer. The owner saw yellow text before the game started, but console visibility/output/colors vary. **Yellow text is not a universal success condition.**
4. Do not close the console while initialization is actively progressing. Wait until the **actual game menu appears**, then close the game normally.
5. Only then extract/copy the Thai mod's BepInEx folder to the same EXE directory. Launch again → **Settings → Language → ไทย**.

If initialization errors/stops or the menu never appears, retain console errors/screenshots and available logs, such as BepInEx/LogOutput.log or .txt and ErrorLog.log, before retrying. Do not infer success from a color, disable security or reset data/Registry by guesswork. [Official IL2CPP instructions](https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html)

## 4. Install the Thai mod

1. Use the full-mod button or the Assets section on [GitHub Releases](https://github.com/IsAmArt/Behind-the-Frame-The-Finest-Scenery---MOD-Thai/releases) to download `BehindTheFrameThai_v1.0.0-rc1_FULL.zip`, not the automatically generated Source code archives.
2. Right-click the mod ZIP → **Extract All… → Extract**, outside the game folder.
3. Open `BehindTheFrameThai_v1.0.0-rc1_FULL`. Locate **BepInEx** beside README.
4. Right-click that **BepInEx** folder → **Copy**, then open the folder with **Behind the Frame.exe** and **Paste**, merging the folder. Do not paste inside the existing BepInEx folder.
5. Check that there is no **BepInEx/BepInEx** nesting and only one Thai plugin version. Existing users must follow [backup/update instructions](BACKUP_UNINSTALL_EN.md) before replacing this mod's files. Preserve other mods and back up your own mod config before deciding which settings to retain.
6. Launch through Steam or Epic Games Launcher; choose **Settings → Language → ไทย**.

After installation (schematic, selected files only):

```text
folder containing Behind the Frame.exe/
├─ Behind the Frame.exe
├─ winhttp.dll                         ← official BepInEx
├─ doorstop_config.ini                 ← official BepInEx
├─ dotnet/                             ← official BepInEx
└─ BepInEx/
   ├─ core/                            ← official BepInEx
   ├─ config/dev.modthai.behindtheframe.diagnostics.cfg
   └─ plugins/
      ├─ BehindTheFrameThai.Diagnostics.dll
      ├─ tamolly_font.bundle
      └─ BehindTheFrameThai/
         ├─ Localization/Language_-_Thai.csv
         └─ VisualLocalization/
            ├─ Thai/                   ← 34 images
            └─ CinemaThai/             ← 12 frames
```

## 5. Settings and safety

All four Development flags are false. Keep ThaiLegacyShaper/ThaiFontScaling enabled; main/language-menu scale1.2, subtitle1.4, others1. No config editing is needed for first installation. Never disable Thai shaping as a black-screen fix. Select language before Cinema; changing it during animation is untested. Missing/invalid visuals may use existing English fallback within its original scope; audio is unchanged. Do not rename/re-save PNGs.

[Known Issues](../KNOWN_ISSUES.md) · [Troubleshooting](TROUBLESHOOTING_EN.md) · [Backup/uninstall](BACKUP_UNINSTALL_EN.md). This exact public package still needs complete user runtime QA. Basic runtime testing succeeded on both Steam and Epic Games Store on Windows x64, confirmed by the project owner on31October2026. This is not complete regression QA or every-build support, and binaries are not claimed identical. No save/Steam Cloud edits are part of installation.
