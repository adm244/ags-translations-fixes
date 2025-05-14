# Unavowed fixes

This folder contains script fixes for "Unavowed".

Tested on version 1.1.1 (Steam). Version number taken from in-game main menu (string in `GlobalScript.scom3`).

## Issues

This game has several issues with translations:

- [x] Missing translation in dialog options with substitutions in their text.
- [x] Missing translation of flashing text when picking items.
- [x] Missing translation for background speech texts because of inserted line breaks.
- [x] Missing translation for diary texts.

## Changes

- CustomDialog.scom3:
    - Added `GetTranslation` into `CustomDialogGui::_addOption` function for each string replacing `$FRIEND1`, `$FRIEND2`, `$HIMHER1`, `$HIMHER2` (fixed typo, unused), `$HQMTGORIGIN`, `$ORIGINPLACE`, `$AORIGIN`, `$MANWOMAN`, `$HESHE`, `$HIMHERME`, `$HISHERME` and `$l_HESHE`.

- Flashtext.scom3:
    - Added `GetTranlation` into `doFlashInv` function for both parts of `String::Append`.

- GlobalScript.scom3:
    - Added `GetTranslation` into `setSmithPage` function for each diary entry.

- LineBreak_200.scom3:
    - Added `GetTranslation` into `InsertLineBreaks` function.
