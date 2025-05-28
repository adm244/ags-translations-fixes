# Old Skies fixes

This folder contains script fixes for "Old Skies".

Tested on version 2.0 (GOG). Version number taken from "vernum.osk" file.

## Issues

This game has several issues with translations:

- [x] Text displayed with the "typewriter" animation is only translated after animation is complete (both "new location" and "current place and time").
- [x] Incorrect speech bubble size if translated text is much longer or shorter than original.
- [x] Missing translation for text displayed with "Character::GSay" function because line breaks were inserted.
- [x] Missing translation for background speech text.
- [x] Missing translation for "Personic", "News" and "E-mail" GUIs (see [Notes](#news-and-emails)).
- [x] Missing\broken translation of historic archive search (see [Notes](#historic-archive)).

## Changes

- BackgroundDialog.scom3:
    - Added `GetTranslation` call to `Character::BGSay` function replacing existing argument.

- FutureSearch.scom3:
    - Added `GetTranslation` call to `getNoteString` function on return string.
    - Added `GetTranslation` calls to `futureSearch` function for each string comparison.

- Personic.scom3:
    - Added `GetTranslation` call into `personicDisplay` function for each argument into `String::Format`.

- TalkyManager.scom3:
    - Added `GetTranslation` call to `Character::GSay` function replacing existing argument.

- typewriter.scom3:
    - Added `GetTranslation` call to `Typewriter::Type` function replacing existing argument.
    - Added `GetTranslation` call to `mySlate` function replacing existing argument.

## Notes

In main menu you can press `ctrl+b` (twice) and type `oldbugs` to access debug menu that will allow you to skip to certain chapters.\
Use this instead of save files to test translation.

### News and Emails

For `FiaEmailManager.asc` email content strings you have to manually concatenate them in *.trs for translation to work.\
For example this
```
<Rosha> Hi everyone! My name is Rosha. I was recruited a few months ago. I'm originally from Spain and just got assigned to the London branch.[[
<Rohn> Hey.[[
<Duffy> Welcome! Ten year veteran of time wrangling here. Based in New York.[[
<Balee> Hong Kong field agent here. Been involved with CZ from the start.[[
<Nozzo> I also joined at the start, but spent the last ten years as a chrono-monitor for the New York office.[[
<Horris> Former field agent, now a freshly minted chrono-monitor in Oslo.[[
<Rosha> Nice to meet you all!![[
```
would become
```
<Rosha> Hi everyone! My name is Rosha. I was recruited a few months ago. I'm originally from Spain and just got assigned to the London branch.[[<Rohn> Hey.[[<Duffy> Welcome! Ten year veteran of time wrangling here. Based in New York.[[<Balee> Hong Kong field agent here. Been involved with CZ from the start.[[<Nozzo> I also joined at the start, but spent the last ten years as a chrono-monitor for the New York office.[[<Horris> Former field agent, now a freshly minted chrono-monitor in Oslo.[[<Rosha> Nice to meet you all!![[
```

> [!NOTE]
> I could've patched `FiaEmailManager.scom3`, but then translated strings would be stored in save files.

Same applies to `NewsManager.asc` content strings.

> [!WARNING]
> Save files store news and emails (as part of a script state), so test translation only on fresh "new game".

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
Both can be translated as long as this rule applies.

> [!WARNING]
> Save files store search entries (as listbox items), so test translation only on fresh "new game".

Some search results are concatenated using `String::Append` before displaying (like `breakdown boys`), so you would have to concatenate them in *.trs file similar to "News and Emails" strings.
