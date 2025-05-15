# Kathy Rain fixes

This folder contains script fixes for "Kathy Rain".

Tested on version 1.0.4 (Steam). Version number taken from in-game main menu.

> [!WARNING]
> This patch contains changes specific to Russian language.

## Issues

This game has several issues with translations:

- [x] Bitmap font doesn't contain necessary glyphs
- [x] Missing language choice in main menu

> [!NOTE]
> Bitmap fonts for Russian version are not included since they aren't made by me.

## Changes

- GlobalScript.scom3:
    - Added Russian alphabet glyphs into `SetupSpriteFonts`, `SetupComputerFont`, `SetupComputerFont2` and `SetupSpeechFont` functions with translation filename check (so that other languages can also work).
    - Added call to `SetupSpriteFonts` into `on_language_change` function (to allow switching Russian and non-Russian glyphs dynamically).
    - Added Russian language with ID 244 in `lb_Languages_OnSelectionChange` and `on_event` (so people can scroll through languages including Russian).
    - Added Russian language check in `game_start` to prevent French and Spanish language names using remapped glyphs (in other words this fixes Cyrillic characters appearing in "Français" and "Español" literal strings in game menu when Russian language is selected).
