# Old Skies fixes

This folder contains script fixes for "Old Skies" (GOG).

Tested on version 2.0 (Steam, GOG). Version number taken from "vernum.osk" file.

## Fixed issues

When it comes to translations, this game is just broken:

- [x] Text displayed with the "typewriter" animation is only translated after animation is complete (both "new location" and "current place and time").
- [x] Incorrect speech bubble size if translated text is much longer or shorter than original.
- [x] Missing translation for text displayed with "Character::GSay" function because line breaks were inserted.
- [x] Missing translation for background speech text.
- [x] Missing translation for "Personic", "News" and "E-mail" GUIs.
- [x] Missing translation for save names.
- [x] Missing translation for lock number search in chapter 1.
- [x] Missing translation for inventory items in chapters 4 and 6.
- [x] Missing translation for confession and chat logs in chapter 5.
- [x] Missing translation for location descriptions on map in chapter 6.
- [x] Bug with fully transparent "new location" animation.
- [x] Broken string comparisons.
- [x] Missing\broken translation of historic archive search (see [Notes](#historic-archive)).
- [x] "Stuck on repeat" button hover sound effect for translated top panel buttons.

## Changes

- BackgroundDialog.scom3:
    - Added `GetTranslation` call to `Character::BGSay` function replacing existing argument.

- Commentary.scom3:
    - Added `GetTranslation` calls to `playComm` function.

- DialogScript.scom3:
    - Added `GetTranslation` call to `_run_dialog102` function for time string comparison in chapter 4.

- Emails.scom3:
    - Added `GetTranslation` calls to `generateVillageEyeMail` function for email sender\recipient, title, date and body.
    - Added `GetTranslation` calls to `generateImaniMail` function for email sender\recipient, title, date and body.
    - Added `GetTranslation` calls to `GenerateAndyMail` function for email sender\recipient, title, date and body.

- FiaEmailManager.scom3:
    - Added `GetTranslation` calls to `generateFiaEmails` function for chat name and content.

- FutureSearch.scom3:
    - Added `GetTranslation` call to `addInfo` function for string parameter.
    - Added `GetTranslation` calls to `addRanking` function for string parameters.
    - Added `GetTranslation` calls to `addDates` function for string parameters.
    - Added `GetTranslation` call to `addEmployment` function for string parameter.
    - Added `GetTranslation` calls to `addCauseOfDeath` function for string parameters.
    - Added `GetTranslation` calls to `addSpouse` function for string parameters.
    - Added `GetTranslation` calls to `addKids` function for string parameters.
    - Added `GetTranslation` calls to `addHomes` function for string parameters.
    - Added `GetTranslation` call to `addButton` function for string parameter.
    - Added `GetTranslation` call to `getNoteString` function on return string.
    - Added `GetTranslation` call to `raGetMitchellRecord` function for string append parameter.
    - Added `GetTranslation` calls to `futureSearch` function for each string comparison.
    - Added `GetTranslation` calls to `fieldGuideSet` function for each string append parameter.
    - Added `GetTranslation` calls to `historyGuideSet` function for each string append parameter.
    - Added `GetTranslation` calls to `processNozzoButton` function for some string parameters.
    - Added `GetTranslation` calls to `raGetMitchellRecord` function for string parameters.

- GlobalScript.scom3:
    - Added `GetTranslation` call to `doTutorial` function for string parameter.
    - Added `GetTranslation` calls to `doTutorial` function for some strings.
    - Added `GetTranslation` calls to `doSerialNumberSearch` function for string parameters.
    - Added new helper function `StrSplit` to split string.
    - Added `StrSplit` and `GetTranslation` calls to `btnSprayGenerate_OnClick` function.
    - Added `GetTranslation` calls to `btnChatLog5_OnClick` function for string parameters.
    - Added `GetTranslation` calls to `readConfession` function for string parameters.

- NewsManager.scom3:
    - Added `GetTranslation` calls to `setFiaNewsItem` function for news title and content.

- Personic.scom3:
    - Added `GetTranslation` call into `personicDisplay` function for each argument into `String::Format`.

- TalkyManager.scom3:
    - Added `GetTranslation` call to `talkNozzo` function for string parameter.
    - Added `GetTranslation` call to `talkImani` function for string parameter.
    - Added `GetTranslation` call to `Character::talkHolo` function for string parameter.
    - Added `GetTranslation` call to `Character::talkFake` function for string parameter.
    - Added `GetTranslation` call to `Character::GSay` function replacing existing argument.
    - Added `GetTranslation` call to `Character::subVocal` function for string parameter.

- TwoClickHandler.scom3:
    - Added `GetTranslation` calls to `changeLblText` function for string parameter and some strings. "Stuck" sound fix.
    - Added new helper function `StrSplit` to split string.
    - Added `StrSplit` and `GetTranslation` calls to `GetInvDesc` function.

- typewriter.scom3:
    - Added `GetTranslation` call to `Typewriter::Type` function replacing existing argument.
    - Added `GetTranslation` call to `mySlate` function replacing existing argument.
    - Added `GUI::set_Transparency` call to `Typewriter::Type` function to fix (rare?) transparency issue before animation.

## Notes

> [!WARNING]
> Prefer ASCII encoding for translation file. The 3.6.1 engine used by the game can read only 1023 bytes from TRA file (lower than legacy versions like 3.2.1).
> UTF-8 encoding effectively halves this limit to ~511 symbols per line (depending on the language). Due to some texts in the game being longer than 700 symbols (such as the confession in chapter 5), your translation will likely get truncated.

In main menu you can press `Ctrl+B` (twice) and type `oldbugs` to access debug menu that will allow you to skip to certain chapters.
In this menu you can press `Ctrl+N` to get access to more options (like accessing sub-chapters and additional debug menus). Also, by pressing `Ctrl+X` you can teleport to a specific room.\
Use this instead of save files to test translation.

> [!WARNING]
> When you start chapters\sub-chapters from a debug menu some initial state differs from normal walkthrough. In this case your best bet is to start from the last sub-chapter of previous chapter.

Do **NOT** translate **any** strings from these scripts:
```
IniFile.asc
fancy.asc
rellax.asc
TotalLipSync-0.5.asc
SpeechBubble.asc
LineBreak_200.asc
MultiResponse.asc
RainModule.asc
CustomDialogGui.asc
TalkyManager.asc
Animations.asc
PauseModule.asc
suitChanger.asc
BackgroundDialog.asc
rewind.asc
```

### Emails (chat logs)

Some emails (like in Winera) have duplicate senders\recipients visually, but are technically different strings with added trailing spaces. These strings affect which message body will be displayed when clicked on email, so **make sure** to match any trailing spaces otherwise emails will be duplicated!

Example strings (trailing spaces were replaced with `*`):
```
Yvonne Lozzotti
Yvonne Lozzotti*
Yvonne Lozzotti**
Yvonne Lozzotti*****
// <...>
Me
Me**
Me***
// <...>
Joe Demarco
Joe Demarco*
Joe Demarco**
// etc...
```

### Historic archive

Search entries in `FutureSearch.asc` are combined and lowercased forming a final search query. Make sure each entry equals to some part of a final query when lowercased. \
For example, these search entries
```
Joseph
Anderson
```
when combined and lowercased must be equal to one of these queries
```
joseph anderson
anderson joseph
```
Both can be translated as long as this rule applies.\
Simply put, make sure to match original strings case and keep names consistent.

For example:
```
Joseph
Джозеф
Anderson
Андерсон
joseph anderson
джозеф андерсон
anderson joseph
андерсон джозеф
```

> [!WARNING]
> Save files store search entries (as listbox items), so test translation only on fresh "new game".
