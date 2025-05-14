# A Golden Wake fixes

This folder contains script fixes for "A Golden Wake".

Tested on version ??? (Steam). Version number taken from ???.

> [!NOTE]
> I'm not sure which version I patched, but it was using AGS 3.5.0.25.

## Issues

This game has several issues with translations:

- [x] Missing translation for options in persuasion minigame.
- [x] Default text for options description in persuasion minigame if options are translated.

## Changes

- GlobalScript.scom3:
    - Added `GetTranslation` into `Convobutt1_OnClick`, `Convobutt2_OnClick` and `Convobutt3_OnClick` functions for each option.

- MouseLabel.scom3:
    - Added `GetTranslation` into `repeatedly_execute_always` for each option.
