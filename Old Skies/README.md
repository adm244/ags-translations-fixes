# Old Skies fixes

This folder contains script fixes for "Old Skies".

Tested on version 1.3 (GOG). Version number taken from "vernum.osk" file.

## Issues

This game has several issues with translations:

- [x] Text displayed with the "typewriter" animation is only translated after animation is complete.
- [x] Incorrect speech bubble size if translated text is much longer or shorter than original.
- [x] Missing translation for text displayed with "Character::GSay" function because line breaks were inserted.
- [x] Missing translation for "Personic", "News" and "E-mail" GUIs.

## Changes

- typewriter.scom3:
    - Added `GetTranslation` into `mySlate` function.

- TalkyManager.scom3:
    - Added `GetTranslation` into `GSay` function rewriting original passed text.

- Personic.scom3:
    - Added `GetTranslation` into `personicDisplay` function for each argument into `String::Format`.
