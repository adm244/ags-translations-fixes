# Unavowed fixes

This folder contains script fixes for "Unavowed".

Tested on version 2.0.0, Steam build 23529477. Version number taken from in-game main menu (string in `GlobalScript.scom3`).

## Fixed issues

This game has several issues with translations:

- [x] Missing translation in dialog options with substitutions in their text.
- [x] Missing translation of flashing text when picking items.
- [x] Missing translation for background speech texts because of inserted line breaks.
- [x] Missing translation for some Jordon journal texts.
- [x] Missing translation for some bank email texts.
- [x] Missing translation for diary texts.
- [x] Missing translation for dragon teeth numbers.
- [x] Missing translation for typewriter text.

## Changes

- CustomDialog.scom3:
    - Added `GetTranslation` into `CustomDialogGui::_addOption` function for each string replacing `$FRIEND1`, `$FRIEND2`, `$HIMHER1`, `$HIMHER2` (fixed typo, unused), `$HQMTGORIGIN`, `$ORIGINPLACE`, `$AORIGIN`, `$MANWOMAN`, `$HESHE`, `$HIMHERME`, `$HISHERME` and `$l_HESHE`.

- Flashtext.scom3:
    - Added `GetTranlation` into `doFlashInv` function for both parts of `String::Append`.

- GlobalScript.scom3:
    - Added `GetTranslation` into `setSmithPage` function for each diary entry.
    - Added `GetTranslation` into `compPage1` function.
    - Added `GetTranslation` into `jordonPW_OnActivate` function.
    - Added `GetTranslation` into `emailBankPage` function.

- LineBreak_200.scom3:
    - Added `GetTranslation` into `InsertLineBreaks` function.

- TwoClickHandler.scom3:
    - Added `GetTranslation` into `getGuiPillarDesc` function.

- Typewriter.scom3:
    - Added `GetTranslation` into `Type` function.
