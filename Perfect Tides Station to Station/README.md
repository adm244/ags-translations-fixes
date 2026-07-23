# Perfect Tides: Station to Station

This folder contains script fixes for "Perfect Tides: Station to Station".

Tested on Steam build 24317713 (21 July 2026), v1.0.13.

> [!NOTE]
> This patch supports multiple languages.

## Issues

This game has following issues with translations:

- [x] Display bubble calculates its size based on untranslated text.

## Changes

### Script changes

- GlobalScript.scom3:
    - Added `GetTranslation` call to `DisplayNoBlock` function replacing existing argument.
    - Added `GetTranslation` call to `ChapterDisplay` function replacing existing argument.
    - Added `GetTranslation` call to `DisplayAtBottom` function replacing existing argument.
    - Added `GetTranslation` call to `DisplayTop` function replacing existing argument.
    - Added `GetTranslation` call to `ComputerDisplay` function replacing existing argument.
    - Added `GetTranslation` call to `DisplayThink` function replacing existing argument.
    - Added `GetTranslation` call to `DisplayThinkAt` function replacing existing argument.

## How to use

1. Inject `GlobalScript.scom3` into `game28.dta`.
2. Place modified `game28.dta` in root game folder.
3. Change `acsetup.cfg` so game would load your `*.tra` file:
```ini
[language]
translation=<tra_filename>
```

> [!NOTE]
> If changing `acsetup.cfg` located in root game folder doesn't have any effect then modify `acsetup.cfg` located at `%USERPROFILE%\Saved Games\<game_name>`.
