# Install the Thai mod — step by step

[Home](../README_EN.md) · [ภาษาไทย](INSTALL_TH.md) · [Troubleshooting](TROUBLESHOOTING_EN.md)

**Full Content — Public Pre-release.** Complete Thai content, incomplete exact-package gameplay QA and known issues. The user performs every game launch.

## 1. Before you start

You need the Steam game on Windows x64, the separate **BepInEx 6.0.0-be.788 Unity.IL2CPP-win-x64 ZIP**, the **Thai mod ZIP**, and Windows **Extract All…** or a ZIP-capable application. BepInEx and the Thai mod are **two different downloads**. The base game should already launch normally. No New Game, save reset or standalone font installation is required. Existing mod users should [back up first](BACKUP_UNINSTALL_EN.md).

## 2. Find the actual game folder

1. Open Steam → **Library**, then right-click **Behind the Frame: The Finest Scenery**.
2. Select **Properties… → Installed Files → Browse…**. File Explorer opens. Some layouts also offer **Manage → Browse local files**.
3. Find **Behind the Frame.exe**. If necessary, open **BehindTheFrame_PC_Steam** one level deeper. Only the folder containing the actual EXE is the destination. Stop if it is missing; do not guess a folder.

[Menu-name reference](https://support.microids.com/en/support/solutions/articles/23000007351-finding-the-executable-file-exe-of-your-pc-game). Steam labels vary by language/version. This is a schematic, not a screenshot:

```text
Behind the Frame - The Finest Scenery/
└─ BehindTheFrame_PC_Steam/
   ├─ Behind the Frame.exe       ← installation destination
   ├─ Behind the Frame_Data/     ← do not install inside this
   └─ …                         ← existing game files
```

Do not use the save, `_Data` or StreamingAssets folder. Trees show relevant files, not the entire game.

## 3. Install BepInEx

1. Click **ดาวน์โหลด BepInEx 6.0.0-be.788** on the README or [download this exact official archive](https://builds.bepinex.dev/projects/bepinex_be/788/BepInEx-Unity.IL2CPP-win-x64-6.0.0-be.788%2B5b766a3.zip).
2. Open Downloads, right-click the ZIP → **Extract All… → Extract**. Windows11 may put commands under **Show more options**.
3. Open the extracted folder until you see **winhttp.dll**, **doorstop_config.ini**, **BepInEx** and **dotnet**.
4. Close the game. Select the archive's contents → right-click **Copy**. Open the folder containing **Behind the Frame.exe**, right-click an empty area → **Paste**. Do not copy the enclosing archive-name folder.
5. Confirm **winhttp.dll** and **BepInEx** sit beside the EXE.
6. Optionally launch through Steam yourself once to check the loader separately and let it generate required files. First startup may take longer than usual.
7. **Close the game before copying the Thai mod.**

If BepInEx or other mods already exist, back up and verify the loader version before replacing anything. Preserve the player's global `BepInEx/config/BepInEx.cfg`. Do not substitute Mono, x86, BepInEx5 or an arbitrary Latest build.

[Official IL2CPP instructions](https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html). Verified archive SHA-256: `F4CC496BD098A0DF4164B81E3737297707F13A47C2478DBA2F60EEFAB784817A`.

## 4. Install the Thai mod

1. Use the full-mod button or the Assets section on [GitHub Releases](https://github.com/IsAmArt/Behind-the-Frame-The-Finest-Scenery---MOD-Thai/releases) to download `BehindTheFrameThai_v1.0.0-rc1_FULL.zip`, not the automatically generated Source code archives.
2. Right-click the mod ZIP → **Extract All… → Extract**, outside the game folder.
3. Open `BehindTheFrameThai_v1.0.0-rc1_FULL`. Locate **BepInEx** beside README.
4. Right-click that **BepInEx** folder → **Copy**, then open the folder with **Behind the Frame.exe** and **Paste**, merging the folder. Do not paste inside the existing BepInEx folder.
5. Check that there is no **BepInEx/BepInEx** nesting and only one Thai plugin version. Existing users must follow [backup/update instructions](BACKUP_UNINSTALL_EN.md) before replacing this mod's files. Preserve other mods and back up your own mod config before deciding which settings to retain.
6. Launch through Steam; choose **Settings → Language → ไทย**.

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

[Known Issues](../KNOWN_ISSUES.md) · [Troubleshooting](TROUBLESHOOTING_EN.md) · [Backup/uninstall](BACKUP_UNINSTALL_EN.md). This exact public package still needs complete user runtime QA. Only the historical Steam Windows x64 setup was tested; **Epic is not supported/has not passed QA**. No save/Steam Cloud edits are part of installation.
