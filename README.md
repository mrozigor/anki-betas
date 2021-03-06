# Anki 2.1 Betas

## Downloads

:warning: This is a beta release. Please back up your collection before trying
it, take regular backups, and make frequent use of the check database feature
until this update has received more testing.

:warning: After using this beta, if you wish to open your collection with an earlier
beta or Anki release, please go to the File>Switch Profile menu item, and click
on "Downgrade & Quit". If you skip this step, you may get an error message when
opening your collection in an older Anki version, and you will need to return to
the latest version, downgrade, then try again.

You can get the latest beta from https://apps.ankiweb.net/downloads/beta/

## Problems

If you run into any issues, please let us know on the beta testing section of
our support site:

https://anki.tenderapp.com/discussions/beta-testing

## Changes

### Changes in 2.1.28beta3

Build 93425be8 / 2020-07-07.

- Fix add-on regression (thanks to Evandro).
- Various graph tweaks.

### Changes in 2.1.28beta2

Build cfc33815 / 2020-07-06.

- Various tweaks to the graphs.
- Update local media server (thanks to Evandro).
- Use Qt colour picker on Linux (thanks to Andreas).
- Fix some add-ons being broken.
- Other minor fixes.

### Changes in 2.1.28beta1

Build 4d23a69e / 2020-07-01.

- The stats screen has been rewritten - feedback on the beta thread would
  be appreciated.
- The old stats are accessible by shift+clicking on Stats.
- Add edited:x search for matching notes edited in last x days.
- Improvements to mpv handling (thanks to Kelciour).
- Windows build fix (thanks to Evandro).
- Various other fixes, including contributions from BlueGreenMagick, Arthur, neitrinoweb
  and kenden.

### Changes in 2.1.28alpha3

Build f44597bb / 2020-06-09.

- The standard Mac build now uses Qt 5.15 - please report any regressions. The
  file size is a bit larger than it needs to be, and may be improved in the
  future.
- The Linux build now uses Qt 5.15 - please report any regressions.
- DB check now shows progress.
- Fixed duplicate/empty field check.
- Fixed audio being included in FrontSide.
- Clearer error message on failed regex search.
- Find & Replace remembers input (thanks to Evandro).
- Code improvements (thanks to BlueGreenMagick, Thomas and Andrew).
- Support input.conf for mpv
- Fixed '&' being changed in image filenames in HTML editor.
- Fixed exports getting broken by Windows carriage returns in note fields.
- Miscellaneous other fixes.

### Changes in 2.1.28alpha2

Build ebce044b / 2020-06-02.

Reworked collection syncing. Some warnings:

- While it has had some testing, please take frequent backups, and keep an eye
  out for (and report) any problems.
- The checking stage at the end of the sync may be slower than normal, as some
  checks that are normally disabled have been re-enabled for safety.

Sync changes:

- Normal syncs and media syncs can operate in parallel, speeding up startup and shutdown.
- Normal syncs no longer need to close open windows like the Browse screen, or close & re-open
  the collection.
- Full syncs now show a progress bar.
- Full syncs can now be cancelled, and both normal and full syncs cancel more quickly.

Other changes:

- Windows standard version has been updated to Qt 5.15.
- Audio player on Windows has been switched back to mpv. Please report any
  issues you have playing audio files/videos.
- Fixed deck deletion, and allow "deleting" the default deck (it comes back empty).
- Fixed custom study not saving.
- Card layout screen divider can now be adjusted (thanks to Evandro).
- Fixed duplicate rendering in card layout screen (thanks to Evandro).
- Fix for a previewing issue (thanks to Evandro).
- Fixed off-by-one in field drag&drop (thanks to BlueGreenMagick)
- Other minor fixes.

### Changes in 2.1.28alpha1

Build 97eadb78.

- Performance improvements to:

  - Startup and shutdown (the first startup will be slow as your collection is updated).
  - The Browse screen.
  - The deck list.
  - The note types screen.
  - The card templates screen.
  - The database check.

- Card generation changes:

  - Card generation now supports negated conditionals, and a mix of required
    and optional fields.
  - When adding/importing, if a normal note doesn't generate any cards, Anki
    will now add a blank card 1 instead of refusing to add the note.
  - Please bear in mind that if you take advantage of these features, older Anki
    clients may report the cards are blank, or try to clean them up when you
    use the Empty Cards feature.
  - Cloze numbers over 499 are no longer supported.

- Card template screen:

  - Changes are now accumulated, and can be saved or discarded when you close the screen.
  - The front, back, and styling are no longer shown at the same time. You can switch between them with ctrl+1/2/3 or cmd+1/2/3.
  - Added a search bar to search for text in the template or styling.
  - Added a dropdown to change the previewed cloze number.
  - Added a checkbox to toggle the filling of empty fields for preview.
  - You can now delete a card template even if some notes are only using that
    template - they will be given a blank card 1 instead.

- Scheduling:

  - The deck list no longer caps counts to 1000.
  - The overview and study screen no longer caps counts to 1000.
  - The deck list will no longer show a parent count higher than the limit
    set on the parent.

- Empty cards screen:

  - Notes will not be deleted by default.
  - Empty cards are grouped by note type.
  - Empty cards can be clicked on to reveal them in the browse screen.

- Database check:

  - Notes with the wrong field count are now recovered instead of being deleted.
  - Notes with missing note types are now recovered instead of being deleted.
  - Notes with missing cards are now recovered instead of being deleted.

- Unicode normalization:

  If you are studying rare CJK characters and wish to prevent them from being converted into
  modern equivalents, the following in the debug console will stop Anki from normalizing note text.

  ```
  mw.col.conf["normalize_note_text"] = False
  ```

Other changes:

- Fields screen now accumulates changes, which can be saved or discarded when you close the screen.
- Updated a few screens to show progress bars instead of hanging the UI.

### Changes in 2.1.24beta9

Build 359b9f5c.

- You can use `w:something` to search on word boundaries, eg:
  - `w:dog`  
    search for "dog" on a word boundary - will match "dog", but not "doggy"
    or "underdog".
  - `w:dog*`  
    will match "dog" and "doggy", but not "underdog".
  - `w:*dog`  
    will match "dog" and "underdog", but not "doggy".
- Fixed clicking on links in add-on configuration documentation.

### Changes in 2.1.24beta8

Build 683f664d.

- Fixed adding and removing deck option groups.

### Changes in 2.1.24beta7

Build ec6c0f86.

- Move the scheduling options in the preferences to a separate tab, so options
  fit on the screen even on devices with small screens.
- Fix pauses caused by a regression in the previous beta.

### Changes in 2.1.24beta6

Build 394f7c63.

This beta changes the macOS dark mode handling of the standard build:

- Anki now solely relies on the night mode setting in the preferences to decide
  whether to show in light or dark mode. Some users wanted to run Anki in light
  mode while keeping the rest of their system dark, and there were various
  display problems when dark mode was changed after Anki started that couldn't
  be easily worked around.
- Users who only use dark mode, and preferred the native look of widgets in dark
  mode, can achieve the previous appearance by running the following command in
  the terminal:

  ```
  defaults write net.ankiweb.dtop NSRequiresAquaSystemAppearance -bool no
  ```

  And the following in the debug console:

  ```
  mw.pm.meta["dark_mode_widgets"] = True
  ```

  This is hidden behind a debug console command because it requires the
  user ensure their system is always set to the same light/dark mode
  as Anki.

Other changes:

- The macOS standard build is built with a newer SDK. If you notice any regressions, please let me know.
- Fixed Anki closing after a full sync on collection load.
- Fixed an error being shown when replaying audio.
- Fixed filtered decks displaying an error in older Anki versions after downgrading.
- Fixed add-ons with multiple branches not updating properly.
- Change the way cloze deletions in RTL fields are handled, which should address some corner cases.
- Fix editor buttons not being highlighted (thanks to Simone).
- Improve invalid HTML/JS error messages (thanks to Evandro).
- Fixed a useless log file being created when exporting.
- Allow selecting add-on config help text (thanks to ijgnd).

### Changes in 2.1.24beta5

Build 0c5f22f4.

- New load/save handling for note types and decks. This should be transparent;
  if you notice any issues, please let me know.
- Avoid scrolling if the selected browser row is still visible after an operation.
- Handle renamed cloze fields when previewing (thanks to BlueGreenMagick).
- Fix a case where decks could be sorted incorrectly (thanks to Arthur).
- Fix some bugs introduced by the recent previewing changes.
- Allow dragging fields to change their position (thanks to BlueGreenMagick).
- Add socks support to media sync.
- Improvements to debug console (thanks to BlueGreenMagick).
- Build improvements (thanks to Evandro).
- Fix deck option changes not marking collection as changed.
- Fix deck_browser_did_render hook.
- Fix interface getting stuck when a corrupt collection was encountered.

### Changes in 2.1.24beta4

Build 16ab351b.

- Updated tag handling:
  - non-wildcard searches now do full unicode case folding (eg 'tag:masse' matches 'Maße').
  - wildcard searches do simple unicode case folding.
  - tag list in browse screen now uses unicode case folding.
- Fix 'is:due' search not combining with other searches properly.
- Fix searches for things like deck:current not reflecting current state.
- Fix duplicate searches.
- Be more tolerant of deck IDs stored in the wrong format by older Anki versions.
- Fix an error that could occur when performing an operation in the browse screen then immediately closing it.
- Clean up the previewing code (thanks to Arthur). Add-ons that modify the preview screen will need updating.
- Prepare for uploading releases to PyPI (thanks to Evandro).
- Improve the handling of deck deletions (thanks to Arthur).
- Avoid decimal place in steps lists where possible.
- Add a compatibility shim for named args to avoid breaking some add-ons.
- Updated config handling. While there should be no immediate breakages, if you're an add-on author and
  store lists or dicts in Anki's config, please see 676f4e74a.

### Changes in 2.1.24beta3

Build d3964603.

Updated the way cards and deck options are loaded and saved. Most add-ons should not be affected,
but a few will need minor tweaks. If you run into any issues and can reproduce them when add-ons are disabled, please let me know.

Other changes:

- Media syncs no longer take time to abort.
- Fixed media sync waiting forever when connection dropped.
- Fixed an issue where regular syncs could fail to end.
- Fixed current card sometimes not being centered when searching.
- Don't force a full sync when DB check finds cards with a high due number.
- A tweak which should fix some broken add-ons from preventing the collection from being loaded.
- GitHub now checks Windows and Mac builds as well (thanks to Evandro).
- More hooks (thanks to Arthur).
- Fix tag searches in custom study (thanks to zjosua).
- Don't throw an error when user has an embedded null in a note field.
- Left-align tags in the browser.
- Ignore .DS_Store files in the media trash folder.
- Remove the check for ':' in DB queries.

### Changes in 2.1.24beta2

Build b1a8107a.

Please see beta 1 for most of the changes.

- The media check will now fix file references in fields that broke because a filename was shortened as part of a sync.
- Fixed error when reviewing (thanks to zjosua).
- Fixed reverse sort order for some browser columns.
- Fixed the UI displaying badly when macOS dark mode changes while Anki is running.
- Don't show a popup when a network error occurs while syncing media.
- Fixed the collection_did_load add-on hook.
- Fixed searches for "(something )" with a trailing space not working.
- Fixed the wrong language shown in the preferences screen for some languages.

### Changes in 2.1.24beta1

Build 9dda5cf6.

2.1.24 focuses on changes to the database layer and searching code.

Searching:

- You can now use `re:something` to search via regular expression, eg:
  - `re:\bdog\b` will search for the word 'dog'. It has a word boundary character (`\b`) at the
    start and end, so it will match 'a dog', but not 'a doggy'.
  - `front:re:t+1` would match "t1", "tt1" and so on in the Front field
  - When searching by regex, unicode case folding is used, so searching for `re:über` will
    show a card that has "Über" on it.
- `nc:something` (short for "no combining") can be used to search while
  ignoring accents, eg `nc:uber` will match both "über" and "Über". This behaves the same way as the "Ignore Accents" add-on, but is about 16x faster.
- You can now sort on the deck, card template, note type and tags columns.
- You can now use wildcards when limiting the search to a field, eg `field*:something`.
- You can now use wildcards when searching for a card template or note type by name.
- `rated:x` searches are now capped to a year instead of a month.
- You can now escaped double-quotes in a search - eg `"foo\"bar"`
- Single-quote searches are no longer supported.
- A version of Advanced Browser that works with this beta
  has been made available [here](https://github.com/ankitects/advanced-browser/releases/tag/2.1.24-fixes). Not everything has been tested, and sorting on some fields will not currently
  work properly.
- Because the searching code has been rewritten, add-ons that modify the search code
  will need to be updated to support 2.1.24. Unfortunately it is no longer possible to override the Finder class - add-ons will need to use the new hooks in the browser screen to either rewrite the search text, or perform their own lookups instead.

Database changes (mainly of interest to add-on developers):

- Anki now uses Rust's sqlite libraries instead of Python's.
- The 'db' object on the collection retains most of the same API as before, minimizing the amount of immediate code changes that are required.
- Some less-used features like named sqlite bindings ("where column = :foo") and custom
  sql functions are no longer supported.
- The old database code remains in db.py, and add-ons can continue to use it for accessing
  their own databases.
- The database is now behind a mutex, and can be safely accessed from a background thread.
- Various screens like the database check have been updated to run on a background thread,
  so they no longer lock up the UI while they're running.
- The database progress handler has been removed. Anki previous had sqlite call back into
  Python periodically during long-running DB operations so it could drain the UI queue,
  but this would vary in choppyness depending on the type of DB operation being performed,
  and it was the cause of some crashes in the past. Add-ons that perform long-running operations
  should instead use mw.taskman.run_in_background() or their own threading solution moving forward.

Other changes:

- Anki will now wait for a media sync to complete or be aborted before closing the collection.
- Fixed progress dialogs failing to appear in a timely manner.
- Allow the type answer arrow to be styled (thanks to Evandro).
- More hooks (thanks to Arthur).

A lot has changed in this beta, so some issues may have slipped through the cracks. If
you run into any problems, please let me know.

### Changes in 2.1.22beta2

Build 0ecc189a.

- Fixed problems playing audio on Windows. Users using the gtts add-on will need to update it.
- Clear the audio queue when moving between cards with autoplay off.
- Fixed play icons not appearing in browser preview when autoplay off.
- Restored grey styling of zeros in the deck list that got lost in the night mode changes.
- Fixed an error shown when running in Spanish.
- Fixed fields containing a filename with non-Latin text from being corrupted when editing HTML (thanks to Evandro).
- Support for validating add-on config schemas (thanks to Arthur).
- Fixed a change that broke some add-ons.
- Fixed the wrong language being selected in the preferences screen.
- Removed the 'too many decks' message in the deck list screen.
- Possible fix for issue playing audio from flash drive.
- Fixed Anki getting stuck when importing an invalid file.

### Changes in 2.1.22beta1

Build 131d37dc.

Please use File>Export to back up your collection with media before trying
this beta. While big problems are unlikely, a backup is always a good thing
to have.

- All the changes from 2.1.21beta1 to 3
- The new timezone handling is now exposed as an option in the preferences
  screen. Please avoid using this if you use AnkiDroid:
  https://anki.tenderapp.com/kb/anki-ecosystem/timezone-handling-changes
- Instead of automatically clearing the media trash after 7 days,
  the media check screen now displays how many files are in the trash
  folder, and allows you to either empty the trash, or restore it back
  into the media folder.
- Fixed repetitive sync errors when long filenames in media folder and
  media check not run.
- More code improvements (thanks to Alan)
- More add-on hooks (thanks to Arthur and Glutanimate)
- More Windows build improvements (thanks to Evandro)
- Rotate log files.
- Ignore http(s) links when checking media.
- Fix a resource leak introduced in an earlier beta.
- Fix inversion of iOS drawings in night mode.

### Changes in 2.1.21beta4

Build f1734a47.

This has been released as 2.1.21 stable without the below changes - please
see the 2.1.21 change notes.

### Changes in 2.1.21beta3

Build 8960d12a.

- Media syncing now logs to collection2.log in your profile folder. If you
  experience any problems with syncing, please attach your log in a support
  ticket and describe the problem (giving an example filename) so I can
  investigate.
- Fix time spans over 12 months not being displayed in years.
- Files deleted via the media check no longer trigger a rescan on next sync.
- Fix the standard Mac build not displaying properly when dark mode active,
  and updated the docs to explain how you can force light mode in Anki while
  system dark mode is active.
- Fix an oversight that was breaking some add-ons unnecessarily.
- More translation work.
- More type hints in the code (thanks to Alan).
- Improvements for building on Windows (thanks to Evandro).
- Support '/' separator in add-on web paths on Windows (thanks to BlueGreenMagick)
- Fix tags that are in the wrong encoding as part of the DB check.
- Display a more helpful warning when mpv/mplayer not installed.

### Changes in 2.1.21beta2

Build 65ec9d19.

- More work on the handling of translations, including tweaks to the way
  the answer buttons and the review history screen show intervals.
- You can now export .apkg files with the V2 scheduler enabled.
- Show next learning card due time, and count for today
- Add-on hook improvements, thanks to Glutanimate and Arthur.
- Hide the default deck in more cases (thanks to Arthur).
- Some improvements to the build process (thanks to Evandro).
- Fixed negative number in "add-on incompatible" message.
- Fixed field contents added by old add-ons like Japanese Support
  not appearing.
- Fixed card info screen not appearing.
- Fixed an error message when using very small learning steps.
- Add "New #" prefix to the due column for new cards.
- Add back missing fcntl for add-ons.
- Fix a race condition in the audio playing code.
- Fixed {{Deck}} showing the filtered deck name instead of the original deck.
- Fixed LaTeX in cloze deletions not being rendered by the media check.
- Cards in night mode now default to dark grey instead of black.
- Fix issue with macOS's dark mode in the alternate Mac build.
- Don't allow scaling of the UI below 100%, as it doesn't work properly.
- Fixed Anki not starting on Windows installs that were lacking TTS support.
- Interrupt current audio even if autoplay is disabled.

### Changes in 2.1.21beta1

Build 683b7983.

Media syncing improvements:

- Media syncing now happens in the background, so you can continue using
  Anki while the media sync completes.
- Aside from syncing at open and close, Anki will sync any media changes
  every 15-20 minutes.
- You can click on the sync button while the spinner is active to monitor
  progress.
- Long filenames and problematic characters should be handled smoothly now,
  instead of causing syncing errors.
- Anki should no longer sometimes forget to download files when a media
  sync fails due to network errors.
- When media files are added within Anki, Anki now marks them
  in the database immediately, which can make things faster for people with
  slower disks if they are not modifying the media folder externally.

Media check improvements:

- The Check Media function now shows progress, and can be interrupted.
- There is now a separate button to generate missing LaTeX.
- If LaTeX fails to build, the problem card will be revealed in the browse
  screen.
- When Anki finds files that are too long or would cause errors on some
  operating systems, it will automatically rename them and update your notes
  to point to the new filename.

Both media sync and the media check now place deleted files in a media.trash
folder inside your profile, instead of placing the files in the system trash.
Any files that have been sitting in that folder for a week or more will be
deleted permanently when you next run a media check.

Other changes:

- Updates to the translation infrastructure - please see https://anki.tenderapp.com/discussions/announcements/138-more-updates-to-ankis-translations
- Improvements to the readability of the scheduling code (thanks to Arthur)
- More hooks for add-on authors (thanks to Arthur & Aristotelis)

### Changes in 2.1.20beta10

Build d0284f75.

For a full list of changes since 2.1.19, please see https://apps.ankiweb.net/docs/changes.html

- Added the ability to export selected notes from the Browse screen, thanks to Arthur.
- Don't filter em/strong tags when pasting.
- Fix rendering of question/answer column in browse screen.
- Clearer error when conditional replacement closing tags are switched.
- Show whether template errors occurred on the front or back template.
- Drawings done in AnkiMobile now appear correctly in night mode.
- Work around HTML editor sometimes failing to appear on macOS.
- Fix error when double-clicking the open profile button.
- Constrain image width in editor to the field width.
- Tweaks to replay audio button alignment/outline.

### Changes in 2.1.20beta9

Build 1fbd925f.

- Standard Windows and Linux builds updated to latest Qt.
- More legible colours in the stats screens in night mode.

### Changes in 2.1.20beta8

Build 5d91580c.

- Emptying a filtered deck in the V2 scheduler no longer unsuspends suspended cards inside it.
- Added an option in the preferences to not interrupt the currently playing audio when answering.
- In night mode, the scrollbar style is now consistent in and out of webviews.
- Lighter buttons and scrollbars in night mode.
- Fix the white lines showing on macOS dark mode in the browse screen.
- Fix some misaligned dialogs in night mode.
- Fix building from a .tar.gz file.

### Changes in 2.1.20beta7

Build 77912aa2/c70badcd/a4764e2a.

- Foreground and background colours in text are now ignored
  when pasting in night mode.
- On macOS, the system theme will be used when dark mode is active.
- Qt has been downgraded to 5.13 on macOS to facilitate the above.
- The audio replay buttons are smaller by default, and can be styled using fill and stroke on '.replay-button svg [circle|path]'.
- Night mode now also used .night_mode - if you notice any problems
  with this please let me know.
- Disabled elastic scrolling in webviews to work around a Qt bug.
- Progress dialogs no longer pop up immediately.
- Minor night mode tweaks.

### Changes in 2.1.20beta6

Build 23f13a31.

- TTS tags now accept a 'speed=1.0' option to control voice speed.
- Adding \{\{tts-voices:}} to your template will show all available voices.
- Replay audio buttons now clickable in card layout and preview screens.
- Fix autoplay of audio in the preview screen.
- Fix Anki filtering spaces out of pasted sound files.
- Fix add-ons being marked as incompatible when they weren't.
- Handle AnkiWeb's new support for multiple add-on versions.

### Changes in 2.1.20beta5

Build d428b3b4.

- Fix issues loading mpv on Mac/Linux.
- Replay buttons now appear in {{FrontSide}}.
- Replay buttons are shown in card layout and preview screens, but
  are not yet clickable.
- More changes to the card display code, which will break more
  add-ons I'm afraid.
- The template hooks have been updated - please see
  https://github.com/ankitects/anki-addons/commits/master for required
  changes.
- A few colour fixes for night mode.
- A change from Arthur that fixes one issue that was breaking add-ons.
- Invert LaTeX in night mode (thanks to zjosua).
- Support specifying min/max versions in .ankiaddon files.

### Changes in 2.1.20beta4

Build 98041059.

- The night mode option now turns the interface dark as well. Please
  report any areas that don't display properly.
- Fix mplayer window popping up on Windows.
- Alter the way negated conditionals are handled in card generation.

### Changes in 2.1.20beta3

Build 95b497cc.

- You can now use `{{tts en_US:Field}}` on your card templates to use the
  text to speech support built into Windows and macOS, changing the language
  code as necessary.
- You can specify the voices you'd prefer - the first available one
  will be used. Eg. `{{tts ja_JP voices=Apple_Otoya,Microsoft_Haruka:Field}}`.
  The voices you specify must match the language.
- In addition to the built in TTS, there is an example add-on that uses gTTS
  available here: https://ankiweb.net/shared/info/391644525
- To see all available voices, use the following in the debug console:

```python
for p in aqt.sound.av_player.players:
  if v := getattr(p, 'get_available_voices', None): pp(v())
```

- Audio buttons are now shown on the card, and can be turned off in the
  preferences. They will show for both regular audio and text to speech.
- Added shortcut keys in the review screen to pause and jump forward/backward
  5 seconds.
- Anki now starts a new copy of mplayer for each audio file on Windows,
  which avoids the need to create temporary files. If you notice any problems
  related to this, please let me know.
- Add-ons that modified the audio code may break with this update.
- For add-on authors, some more examples using the new hook system are
  available on the following page, including ported versions of the clickable
  tags and additional card fields add-ons:
  https://github.com/ankitects/anki-addons/tree/master/demos

### Changes in 2.1.20beta2

Build c9a46268.

- Anki will now check for add-on updates once a day.
- Disabled add-ons are now included in the check as well.
- If a user attempts to install an add-on that doesn't support the version
  they're on, Anki will now prevent them from doing so.
- The 'max supported version' that add-on authors can specify in AnkiWeb
  is now used to prevent users from downloading add-ons that won't work on
  their Anki version, and to disable add-ons when they update to a new version.
- Fix incorrect delay being logged when Hard is used on the first learning step
  in the V2 scheduler.
- The editor no longer modifies percent-escaped text outside of image tags.
- Fix an extra linebreak being left in a field when an image is attached
  to an empty field.

### Changes in 2.1.20beta1

Build fa564772.

- Changes to the way cards are rendered that will break some add-ons - please
  see https://anki.tenderapp.com/discussions/beta-testing/1706-anki-2120-updates-to-card-template-rendering[here]
- A new hook system for add-ons - please see https://anki.tenderapp.com/discussions/beta-testing/1704-anki-2120-updates-to-the-hook-system[here]
- Tweaks to the 'tag updated notes' feature (thanks to Erez)
- Fix cards being sorted in wrong order when added after the note was created (thanks to Arthur)

### Changes in 2.1.17beta8

Build f4fb7319.

- Minimum Python version is now 3.7.
- Updated the way templates are rendered. If you notice any problems or
  messages printed to the console, please post on the support site.
- Double-clicking on .ankiaddon files should now work on Mac and Windows as well.
- Bug fix for tag updated notes feature (thanks to Erez).

### Changes in 2.1.17beta7

Build a4d38d65.

- Added an option to tag updated notes when importing (thanks to Erez).
- Install add-ons by double clicking on their files (thanks to Glutanimate).
  Currently only on Linux; support for Windows/Mac will be added soon.
- The alternate Windows build now uses Python 3.8/Qt 5.12.
- The alternate Mac build now uses Python 3.8.
- The alternate Linux build has been dropped.

A bunch of behind-the-scenes changes to the code in this release. If you
notice any regressions, please post on the beta testing thread.

### Changes in 2.1.17beta6

Build 4cead7ef.

- Added a beta label to the experimental scheduler,
  as a timezone corner case needs to be addressed before
  general release.
- Fixed sidebar background on Windows 10.
- Fixed building from source on 32 bit Linux.
- Fixed alternate template syntax not being recognized.
- Automatically remove ':' from field names when opening the
  card templates screen, as it conflicts with the template syntax.

### Changes in 2.1.17beta5

Build 518cc442.

- Changing large note types is significantly faster.
- Fix a bug that was preventing new profiles from being created.
- Fix a bug in the handling of MathJax+Cloze (thanks to Michal).
- Fix missing border when the user has modified the interface scale.

### Changes in 2.1.17beta4

Build bfcc8379.

The standard Mac and Linux builds have now been updated to the new toolkit
as well - please report any regressions.

### Changes in 2.1.17beta3

Build da942617.

Another Windows-only build.

- Improved the performance of the browse screen's sidebar.
- If you use any add-ons that alter the sidebar, you will need to disable
  them prior to upgrading, as add-on authors will need to modify their code
  to work with the new implementation.
- Added an option in the preferences screen to adjust the UI size.
- Fixed a regression in the way duplicate deck names were handled.

### Changes in 2.1.17beta2

Build ff6b58c2.

A Windows-only build, built with the latest toolkit version. Please report
any improvements or regressions.

If you've previously customized the DPI/Scaling as described on
https://apps.ankiweb.net/docs/knownissues21.html#text-size, please try
running the beta without the customizations and report how you go.

In beta 2:

- Alter the way DPI scaling is handled.
- Remove help button from some Window titles.
- Alter a change made in .16 that could break some editor add-ons.

### Changes in 2.1.17beta1

Build 81bdd860.

A Windows-only build, built with the latest toolkit version. Please report
any improvements or regressions.

### Changes in 2.1.16beta4

Build 4bc33e2f.

- Syncing should work properly now when you change timezones without visiting AnkiWeb.
- Ensure learning cards in filtered decks with 'order due' show in template order.

### Changes in 2.1.16beta3

Build bb62a3c1.

- Remove the 'experimental' label from the new scheduler.
- New installs default to the new scheduler.
- You can now import and export decks with scheduling enabled in the new scheduler.
- Fix bold/italics/underline pasting that broke in the last beta.
- Hide empty Default deck in deck picker (thanks to Arthur).
- Add an extra day to the interval when using Easy on a relearning card.
- Preserve surrounding styling when making cloze deletions.

### Changes in 2.1.16beta2

Build bceb4feb.

- Pasting now includes formatting by default.
- Preserve foreground/background color when pasting.
- Preserve bold/italic/underline when pasting from Google Docs.
- When pasting with the shift key, bold/italics/underline is also stripped.
- Draw preview screen more quickly.
- Fix race condition in preview screen (thanks to Håkon).
- Use --exact with dvsvgm to prevent truncated subscript/superscript in LaTeX.
- Various small fixes.

Thanks to Arthur for contributing a number of fixes:

- Newly created cards could be given the wrong due number.
- Sticky fields were ignored when closing the add card window.
- Adding a note type forced a full sync.
- Remove shortcut keys from translations.
- Documentation changes for translators.
- Case not being preserved when changing a deck's parent.
- Hide default deck in other screens when empty.

### Changes in 2.1.16beta1

Build 2e7b7560.

This build updates the translation handling as part of the move to Crowdin.
Some languages were missing some plural forms in the past - in order to prevent
errors, the missing forms have been copied from the highest previous plural.

If you'd like to contribute to the translation effort, please see
https://apps.ankiweb.net/docs/manual.html#translating-anki

Also:

- Fix qtwebengineprocesses not being cleaned up when stats window closed.
- Allow smaller window when editing current card.
- Support pasting multiple URLs at once.
- Add ability to force software rendering on old Macs (thanks to Mike)
- A fix for case insensitive field name handling in find&replace (thanks to lovac42)
- Fix non-integer intervals being imported from Mnemosyne (thanks to Blauelf)
- Clear undo queue when changing scheduler (thanks to lovac42)
- Default to not closing add window (thanks to Aidan)
- Sort new cards separately when sorting by ease (thanks to Arthur)
- Fix a bug in the V2 scheduler.
- Properly handle backslashes in the replacement section of Find&Replace.

### Changes in 2.1.15beta1

Build 442df9d6.

This is a candidate for the next stable release, so if you encounter any
issues, please let me know as soon as you can.

- The V2 scheduler now fully randomizes review cards due on a given day.
- Fix add-ons errors on Windows when profile path was short.
- Fix flag changes in Browse screen not syncing.
- Cleanup recording wav file when recording canceled.
- Fix the window icon on Wayland (thanks to Wilco).
- Add a progress bar to media deletion.
- Other minor changes.
