# Perfect Tides

This folder contains script fixes for "Perfect Tides".

Tested on 2.0.11 GOG build 57024382676366918 (08 November 2023).

> [!NOTE]
> This patch supports multiple languages.

## Issues

This game has following issues with translations:

- [x] Display GUIs calculate its sizes based on untranslated text.

## Changes

### Script changes

- GlobalScript.scom3:
    - Added `GetTranslation` call to `PTDisplay` function replacing existing argument.
    - Added `GetTranslation` call to `PTDisplayAtY` function replacing existing argument.
    - Added `GetTranslation` call to `PTDisplayAtBottom` function replacing existing argument.

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
