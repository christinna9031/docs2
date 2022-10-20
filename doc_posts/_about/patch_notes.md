---
layout: default
title: Patch Notes
permalink: /patch-notes
menu: About
num: 1
type: fullpage
---

#### SAMMI 2022.4.4

New Features:
- Added JSON checker for when Send OBS Request Command is executed. [Christina]
  - If the JSON is not formatted correctly, you now get an alert, and the request is not sent.
- Added more variables to OBS global variables.
  - port and type [Christina]
  - ip [Chrizzz]
- Added client_language as a global variable [Chrizzz]

Improvements:
- Added 2 new Twitch Scopes (No commands yet, but can be done via HTTP Requests) [Silverlink]
  - Charity Scope
  - Goals Scope
- Optimized Bridge to send default parameters to SAMMI when executing SAMMI methods with empty parameters to prevent SAMMI crashing [Christina]
- When exporting or importing a deck, the lb_version key is now replaced with sammi_version key [Christina]
- SAMMI now automatically fetches data for all OBS connections. [Christinna]
  - the Fetch OBS Data checkbox has been removed from OBS Connections, which should fix several OBS-related crashes.

Removed Features:
- Removed 2 Twitch Scopes [Silverlink]
  - Twitch Stream Key (SAMMI does not need the Twitch Stream Key to operate so we removed this)
  - Edit Follows (This is deprecated by Twitch and does nothing anymore)

UI Changes:

Bug Fixes:
- AM and PM now work correctly in Date/Time commands [Sebas]
- MMM and MMMM tokens now work again [Sebas]
- Daylight Savings Time is now correctly calculated in Date/Time commands [Sebas]
- Fixed "Divide by Zero" crash when minimizing SAMMI window in some cases [Silverlink]
- Fixed "Can't create a surface with either a width or height with a value less than or equal to zero" error [Silverlink]
- Fixed Twitch connection not getting properly removed when token is alread expired [Christina]
- Fixed crashes when users try to access non existing structure in OBS Request response or save the response into non existing objects/arrays. [Christina]
  - It will now show yellow alert messages instead.
- Fixed OBS Set Scene Transition Settings command crash [Christina]
- Fixed several OBSws5 related bugs, including: [Roadie]
  - Source Delte crashes
  - Source Filter removed crashes
  - New scenes and sources not being added to Pull Source Value list, and crashing if the list was open when the scene was made
  - Opening the source dropdown menu after creating/moving sources
- Fixed a crash when Undo was used in some cases in OBS [Christina]
- Fixed a crash when user tried to insert or delete a value in global array from Bridge [Christina]
- Fixed duplicate messages for OBS Connected/Disconnected alerts [Christina]
- Fixed a crash where SAMMI would try to auto-connect to OBS when there were no OBS connections [Sebas]
- Fixed Send OBS Request command having the default wrong JSON payload in some cases [Christina]
- Fixed Send OBS Request command crash when OBS returns no data in its response due to incorrect user input [Christina]
- Fixed a crash when decks are being dragged around while alt tabbing at the same time [Christina]
- Fixed a crash when user attempts to open About Page without being connected to internet [Christina]
- Fixed a crash when trying to uninstall an extension without a bridge connected [Sebas]
- Fixed crashes when Twitch, OBS and YouTube json settings files are either empty or corrupted. [Christina]
  - It now creates default settings and properly alerts the user instead.
- Fixed a bug where, after deleting an OBS connection, the global variable would not be deleted [Christina]
- Fixed SAMMI displaying moderator as 'Unknown' in some Pubsub moderation alerts [Christina]
- Fixed an ocassional crash when saving a deck [Sebas]
- Fixed a crash when an extension sends incorrect data to trigger [Sebas]
- Fixed a crash when a button was incorrectly saved in previous version [Sebas]
- Fixed an About Window Tags bug [Silverlink]

#### SAMMI 2022.4.3

New Features:
- Added Reload Bridge button to the Bridge menu [Christina]
- Added a super secret early-access feature - our Patrons can request access [Christina]
- New Language: French [MisterK]

Improvements:
- Significantly improved how error logs are sent to us and processed - please fill out the comment describing what you were doing when SAMMI crashed as it really helps us narrow it down [Christina]
- Bridge Verify button label in the Update Window changed to Reinstall if Bridge versions match, since in this case it just downloads a clean version of Bridge and reinstalls all extensions [Christina]
- New translations added [Sebas + translators]

Removed Features:
- Twitch Connected/Disconnected Triggers [Christina]

UI Changes:
- Fixed YouTube Connections layout [Sebas]
- Remade many buttons and text layout to allow French translation [Sebas]

Bug Fixes:
- lots of ws5-related bugs have been fixed in this update [various]
  - SceneItemRemoved crash
  - SceneItemCreated crash
  - "obsws5_event line 71"
  - "obsws5_event line 355"
  - OBS Pull Source Value now works again for ws5 users
- Fixed SAMMI Core crashing when it's resized sometimes [Christina]
- Fixed a bug where the most recent Patch Notes wouldn't show [Christina]
- Fixed Twitch token revoke crash [Christina]
- Fixed Pubsub connection issues - it no longer freezes for users with higher ping and the connection is made asynchronously now instead [Christina]
  - pubsub_timeout in settings.ini can be deleted if you previously set it up
- Fixed YouTube Test Triggers for Chat in Bridge having is_member and is_verified pull values swapped [Christina]
- Fixed encrypted decks not saving enabled/disabled state [Christina]
  - if you're toggling this on an encrypted deck, it might slighly lag as it needs to decrypt and encrypt it again
- Fixed crash that sometimes occured on Edit Channel Points command (untested) [Christina]
- Fixed a crash after an OBS Connection was renamed and not found in some cases (untested) [Christina]
- Fixed a crash when version window was closed while an update was downloading [Christina]
- Fixed an occasional crash when SAMMI fails to connect to OBS [Christina]
- Fixed a bug where Source Toggle Mute would cause ws5 connection to drop [wolbee]
- Fixed an occasional crash when opening a menu [Sebas]
- Fixed an occasional crash when opening a dropdown [Sebas]
- Fixed a crash when updating from LB2CE to SAMMI [Sebas]
- Fixed a crash when opening the About window and the language package was not updated [Sebas]
- Fixed incorrect value when using X token as an input format in Date/Time Math [Sebas]
- You can now submit your extensions at sammi.solutions/extensions again [Christina]
- Fixed OBSWS connection freeze [Christina]
- Fixed a high ping crash for Pubsub [Christina] 

Known Bugs:
- For Date/Time commands, using the X token for the input format doesn't take into account Daylight Savings Time

#### SAMMI 2022.4.2

Improvements:
- Made it so that Patrons are only loaded once at the start of SAMMI instead each time you opened the about page [Silverlink]
- Made the requests section of HTTP Request have a dropdown for the most common types of request [wolbee]
  - Other request types can be manually written in, if needed, and all previous commands should still work without any changes needed.
- Change default timeout to 1000 in wait commands [Sebas]

UI Changes:
- Fixed the weird background on the copy / delete buttons in the variable viewer [Silverlink]
- Changed SAMMI Core font in about page to Nunito [Silverlink]
- Gave some buttons some more room for text [Sebas]
- Added translations to the about window [Sebas + translators]

Bug Fixes:
- Fixed Right-Click -> Delete button not working [Sebas]
- Rewrote obsws5_event to address a multitude of crashes [Roadie]
- Fixed visibility toggle crash on data_behavior [Roadie]
- Fixed crash with missing requestId on ws5 [Roadie]
- Fixed the whole "patch notes not deleting, verify update loop" thing [Roadie]
- Fixed a few instances of "missing text" [Sebas + translators]
- Fixed a few commands sharing an error message [Sebas]
- Stopped you being able to name a button Global [wolbee]
- Fixed a crash on start when SAMMI is scaled [Sebas]
- Fixed a bug with menus [Sebas]
- Fixed a crash when command is incorrectly saved [Sebas]
- Fixed a crash on start when SAMMI was already running [Sebas]
- Fixed a visual bug that didn't update copy and delete button when running a button from edit button window [Sebas]

#### SAMMI 2022.4.1

Important note for users who had Pubsub connection issues:
- This update includes a temporary workaround until a "more elegant solution" can be found. If you had Pubsub connection issues, please make yourself known in the Discord, and one of the dev team will instruct you on how to fix it.

New Features
- About page, featuring information on the developers, Patrons, and more. [Dev team]

Improvements:
- Error logs now contain an identifier to help distinguish between repeated reports from the same person or from different people. [Christinna]
  - No personally identifiable information is sent in the report, so reports cannot be linked back to a specific user.
- Shortened the version matching alert. [Sebas]
- Updates to language files. [Translators]

UI Changes:
- Changed SAMMI Background color to #122c52 matching the rest. [Silverlink]
- Changed Bridge Icon. [Christinna]
- The copy buttons in the Variable Viewer now share a background. [wolbee]

Bug Fixes:
- Fixed a double pop-up when updating languages for SAMMI Core. [Christinna]
- Fixed a bug that reloaded decks from within the edit button screen. [Christinna]
- Array Filter and CSV Math should no longer crash when used with strings. [Sebas]
- Revoking your Twitch token should no longer crash. [Roadie]
- Fixed a crash when creating a reward after duping another with Reward ID swap enabled. [Sebas]
- Checking the version should no longer freeze clicking. [Christinna]
- Fixed the Verify update loop. [Christinna]
- Fixed a bug when trying to install an extension when no files are found. [Christinna]
- Fixed a bug when trying to load a backup if no file was selected. [Christinna]
- Fixed a Pubsub crash on moderator action trigger. [Christinna]
- Fixed a crash on InputVolumeChange OBS trigger. [Roadie]
- Fixed a bug when saving decks. [Christinna]
- Fixed a crash on Source Filter name changes. [Roadie]
- Fixed a bug where the SourceID Menu wasn't working as intended. [Roadie and Sebas]
- Fixed a crash on Source Scale change. [Roadie]
- Fixed an bug when copying variables returned undefined. [Christinna]
- Fixed Ctrl + Z and Ctrl + Shift + Z not always working in deck view. [Christinna]
- Fixed Pubsub connection issue (see note at top). [Christinna]
- Fixed a crash when deck size was left blank. [Christinna]

Known Bugs: 
- Button menu option to 'Delete Button' doesn't work currently. Use the keyboard 'Delete' key instead.
- Extension commands for filter boxes do not correctly show source filters.



#### SAMMI 2022.4.0

###### New Features
- Added automatic update checker (you can disable it in the Settings menu), will remind you again in 2 days 
  if there's a new version and you clicked no the last time [Christina]
- Added case-insensitive checkbox in string commands: Replace, Replace All, Position and Count [Sebas]
- Added command to send Twitch Announcements (only default announcements for now, colours coming soon) [Silverlink]
- Added the following shortcuts to the Main Window: [Christina]
  - CTRL+N to create a new deck
  - CTRL+TAB to open/close variable window
- Added the following shortcuts to the Deck Editor Window: [Christina]
  - Double tap on an empty area to create a new button (triple tap to create a new button and enter the edit command screen immediately)
  - CTRL+TAB to open/close variable window
  - CTRL+C to copy a button
  - CTRL+V to paste a button
  - DELETE to delete a button
  - SHIFT+CTRL+Z or CTRL+Y to redo an action
  - CTRL+S to save and exit deck
- Added the following shortcuts to the Command Editor Window: [Christina]
  - CTRL+TAB to open/close variable window to the variables of the button that's currently being edited
- Added new features to the Command Editor Window: [Christina]
  - Save Button - quickly save a button (and the whole deck you're currently editing) without having to exit the command screen window
  - Run Button - quickly save and run a button without having to exit the command screen window
  - Save and Close - save and close a button you're currently editing
  - Cancel - cancel any changes made before pressing Save or Run Button and close a button
- Added CTRL+Left and CTRL+Right to move one word left or right in text boxes [Roadie]
- Added From Channel ID trigger pull value to Trigger Pull command for all Twitch Pubsub and Twitch Chat triggers. 
  This allows you to see which Twitch channel the trigger came from. [Christina]
- Added native Pubsub connection, Transmitter is not required anymore for Twitch connection [Christina]
- Added options to download extensions from 3 external sites (Official Repo, Christinna's Repo and StreamUP.tips) [Silverlink]
- Added the ability for SAMMI to reopen automatically after a crash [wolbee]
- Added the option to save the result of a String Digits Only command as a number instead of a string [wolbee]
- Added "Array Filter" Command - Lets you filter values in an array that fulfil some condition [Sebas]
- Added "Array Map" Command - Lets you make math with every value in the array [Sebas]
- Added "Concat Operator" - Lets you concatenate two values (strings or numbers) [Sebas]
- Added "CSV Column Exists" Command - Checks if a column exists. Returns -1 if it doesn't exist or the column number. [Sebas]
- Added "CSV Math" Command - Lets you find the sum, mean, max and min of a column or row. [Sebas]
- Added "Dev Mode Only" Commands - Set Global Variable, Custom Packet [Christina]
- Added "Object to Array" Command - Lets you convert an object into an array in two different ways: keys or values. [Sebas]
- Added "Date/Time Math" Command - Lets you add or subtract seconds/minutes/hours/days/months/years to a date/time in many different formats. [Sebas]
- Added "Date/Time Diff" Command - Lets you calculate the difference in seconds/minutes/hours/days/months/years between two dates/times in many different formats. [Sebas]
- Added "File: INI to Object" Command - Lets you save all the content of an INI file into an object of objects (each section is an object). [Sebas]
- Added "File: Object to INI" Command - Lets you save all the content of a properly formatted object into an INI file. [Sebas]
- Double clicking on an empty area in a deck will create a new button, triple clicking will create a new button and enter the edit command window [Christina]
- Added localization system to allow SAMMI Core translations [Sebas]
 - Fixed typos in English language [Cyanidesugar]
 - Spanish Translation [Sebas]
 - German Translation [Chrizzz]
- If SAMMI crashes, you can now automatically submit your error log to our developers and leave a comment as well (only available for non button errors) [Christina]
- Added ability for SAMMI to automatically close variable wrapping ("$/") when you open it (by typing "/$") [wolbee]
  - will only work if there is nothing to the right of the cursor, or if the next character is a space
- Can now copy the variable value in Variable Window [Christina]
- Added specific buttons for copying the Variable Value or Variable Path [Silverlink]
- Added a global premade variable deck_connected to check whether SAMMI Deck is connected [Christina]
- Added the following triggers: [Christina]
  - SAMMI Deck Connected - Triggers anytime SAMMI Deck connects 
  - SAMMI Deck Disconnected - Triggers anytime SAMMI Deck disconnects
  - Third Party Connected - Triggers anytime a third party app (i.e. not the official SAMMI Bridge or Deck) connects
  - Third Party Disconnected - Triggers anytime a third party app (i.e. not the official SAMMI Bridge or Deck) disconnects
- Added a check to reduce number of crashes due to email scope missing when doing a Twitch: Get User Info command [wolbee]
- Added Install all Extensions from folder option to Bridge menu - after selecting any file in the selected directory, 
  it will install all the files in the directory. You can decide whether you want to force install them all 
  (will replace the Brigde code + your deck if they're already installed, and ignore any requirements not met, such as minimum SAMMI version
  or Transmitter being connected) or whether you want to decide for each file [Christina]
- Added a super secret shadows setting - put shadows="0.000000" into your settings file to remove shadows in SAMMI [wolbee]
- Added new SAMMI Core icon [Silverlink]
- Added Swap Rewards ID checkbox in the Channel Points Window to swap the ids in all the commands if you dupe a reward [Sebas]

###### Improvements
- Optimized how SAMMI detects double clicking in the first place [Christina]
- Button Settings will no longer allow Queue and Overlap to be checked together. Functionally they conflict with each other [Roadie]
- Create Reward for Twitch now has an option to have the reward enabled or disabled upon creation [Roadie]
- Dropdown list icons to a right arrow, to indicate the open to the right [wolbee]
- Dropdown menu buttons icons to a down arrow, to make them more obvious [wolbee]
- Image paths textboxes to only show the image name. No more confusion when sharing decks with images [Silverlink]
- Left clicking on an empty area in a deck does not show a menu anymore, only when right clicked [Christina]
- Renamed Fetch OBS Data command to Send OBS Request command (serves both for fetching OBS data and sending custom packets to OBS) [Christina]
- Removed Set Global Variable and Custom Packet commands (Previously made buttons with these commands will still work) [Christina]
- "Get Date/Time" Command now lets you get the date/time in a lot of new formats (old commands will still work) [Sebas]
- Increased maximum character limit for extension trigger message text box to 500 characters [Christina]
- Button IDs inside Variable Window are now sorted alphabetically, Variable names can be sorted either by type or alphabetically [Christina]
- Premade variable transmitter_connected has been replaced by bridge_connected. 
  transmitter_connected still exists as a premade variable to maintain backwards compatibility, however it will not be displayed in the variable window anymore. 
  Going forward, we recommend using bridge_connected variable instead. [Christina]
- Modified some trigger names (backwards compatibility maintained, no need to change anything in your buttons) [Sebas + Christina]
  lioranboard Shutdown -> SAMMI Shutdown
  lioranboard Deck Reload -> SAMMI Deck Reload
  lioranboard Reset -> SAMMI Reset
  lioranboard Crash -> SAMMI Crash
  Transmitter/Streamdeck Connected -> SAMMI Bridge Connected
  Transmitter/Streamdeck Disconnected -> SAMMI Bridge Disconnected
  - Note: Streamdeck triggers never worked to begin with, they're separate triggers now in SAMMI
- You will receive a yellow notification message in SAMMI Core if any app (Bridge, Deck, Third Party) tried to connect to SAMMI but could not authenticate [Christina]
- Windows inside SAMMI (like Settings and Button Appearance) can now be moved by dragging anywhere on the top bar, not just the tab [wolbee]
- Transmitter has been revamped and changed to Bridge [Christina]
  - the old Transmitter will NOT work with SAMMI anymore, you must update to Bridge
  - the folder name has also changed from Transmitter to Bridge
  - For extension devs: 
    - old extensions are still fully backwards compatible with SAMMI
    - use .sef instead of .lb2 extension for any new SAMMI extensions
    - Twitch user data is no longer stored in LBVars global variable anymore, you must use SAMMI.getTwitchList() to retrieve information such as Twitch user token 
    - old functions LB.X() still work, however using SAMMI.X() instead is preferred now
    - for further info see https://github.com/SAMMISolutions/SAMMI-Bridge 
- Extension file extension .lb2 has been replaced with .sef (SAMMI Extension File), however SAMMI still accepts both .lb2 and .sef files when installing an extension [Christina]
- Shadows are now more consistent across the program [wolbee]
- Improved command alerts (yellow error messages) to show button id, command name and command position. [Sebas]
- Allow Stream Deck option was completely removed from Settings and is enabled by default now [Christina]
- Made by default that all scopes are selected when authorizing your Twitch account [Silverlink]
  - New Open Twitch Beta scopes are also added but are deselected by default, they may not function or not do anything yet. [Silverlink]

###### UI Changes

- Added a white selected area when clicked on a grid with no buttons in it [Christina]
- Lots of UI improvements for consistency and to allow translations [Sebas]

###### Bug Fixes
- Fixed a bug where single tapping on a button/deck, moving the mouse and single tapping again on another button/deck would open the button/deck 
  if done in quick succession. Now it only opens it if double clicked on the same button/deck. [Christina]
- Fixed a bug where pressing Run while leaving a Delay field empty caused a crash [wolbee]
- Fixed a bug where creating a new source caused an OBSws error alert [wolbee (with help from TheBurge, devin, and Roadie]
- Extension commands for scene and source boxes are now saving their values from the dropdown menu [Christina]
- CSV Set/Get Box commands now escape stringfied objects/arrays [Sebas]
- Extension files can now be both LF and CRLF [Christina]
- Adding required_extension key in your extension file with a stringified array correctly checks for installed extensions now [Christina]
- Fixed YouTube Subscriber event triggering multiple times in a row [Christina]
- Fixed YouTube showing -1 viewers when live in YouTube settings menu [Christina]
- Fixed Bridge generating broken tabs if Extension names have certain invalid characters in them

Known Bugs: 
- Extension commands for filter boxes do not correctly show source filters

#### LioranBoard 2 2022.3.2 CE

###### New Features
- Added the option to disable Enhanced Protection Mode, allowing LioranBoard to modify/delete any file. [Christina]

###### Improvements
- Removed the ability to see your Stream Deck password as plaintext if you disabled the Stream Deck. [Christina]

###### UI Changes
- Updates to the Update Viewer Window [wolbee]
  - Download button now shows if a component is missing
  - Buttons now show "Revert", and Column header shows "Previous", if Latest Version is not ticked
  - Changed status icons
	- green means version numbers match (may still need to Verify though)
	- yellow means update/revert available
	- red means missing

###### Bug Fixes:
- Fixed a bug where the Release Commands warning was cowering behind the Open Docs button. [wolbee]
- Fixed a bug where Revoke Token needed to be clicked twice in order to work. [Christina]

#### LioranBoard 2 2022.3.1 CE

###### Important Security Patch
- Disabled file saving/modification/deletion from folders outside of your main LB directory.
	- The LB Dev team discovered that previous versions of LioranBoard 2 allowed any files on your computer
	to be modified, even if they were outside of the main LB directory. This meant that previously, anyone
	could delete/modify your decks, or any important files on your PC, with a single command.

###### New Features
- Added new Trigger Pull Data value outcome_amount for predictions (returns the amount of outcomes) [Christina]
- Added two new Twitch Moderation Triggers: deny unban request, approve unban request [Christina]

###### Improvements
- Ctrl + Left/Right navigate properly in text boxes [Roadie]
- Updated the alert system to allow for multi-line alerts, including from the Alert Message command [wolbee]
- Delete Key now works when held [Roadie]
- Spelling fixes [Roadie, wolbee & cyanidesugar]
- New Transmitter V6.1 is available [Christina]:
	- Fixed non-existent usernames when testing Twitch triggers
	- If you input custom username in Twitch Chat Message test trigger, it will automatically retrieve user ID to match it
	- Added Twitch Poll, Prediction and Hype Train test triggers (thanks goes to Chrizzz for providing me with example Hype Train payloads)
	- Added YouTube test triggers
	- Changed favicon to our new CE butterfly [wolbee]
	- Note: Twitch test triggers will ONLY work if you're using this new Transmitter with LB version 2022.3.1 or higher
- Changed how YouTube retrieves access tokens, and patched a potential security issue to prevent any other programs from accessing it and potentially depleting the project quota [Christina]

###### UI Changes
- none

###### Bug Fixes
- Fixed high CPU usage bug [Roadie]
- Fixed new extension install bug when using Transmitter V6.X [Christina]
- Get Variable Type now returns "button" if given a button ID instead of a variable [Christina]
- Using Ctrl-Z in a delay box no longer crashes the Receiver [Roadie]
- Updater fixed to check latest and previous forks for most current and second most current release [Roadie]
- Fixed the size of the Wait Until Variable Is command [wolbee]
- Fixed Trigger Pull Data for polls incorrectly returning poll name for poll_id pull value instead of poll ID [Christina]
- Fixed LioranBoard crashing after receiving Twitch deny/approve unban request trigger [Christina]
- Fixed misbehaving text in the Init Variables window when Persistent Variables are off [wolbee]
- Fixed a bug where a button wouldn't get pasted if it went off the grid - you will now be prompted
whether you want LB to resize it and paste it anyway [Christina]

<hr>

#### LioranBoard 2 2022.3.0 CE

###### New Features
- Delete key works in text boxes [Roadie]
- Added option to select a secondary Twitch Client ID [Silverlink] - this is an optional setting for now, but will be required in the future, which will require you to relink Twitch accounts and re-duplicate channel points made with LioranBoard
- Transmitter updated to V6. You can keep using V5 if you do not use the new secondary Twitch Client ID [Christina]
- Added the option to reveal Transmitter in File Explorer [Christina]

###### Improvements
- Automatic Updating works again and is safe to use (only for version 2022.3.0 and up). Huge thanks goes to [Roadie]
- Changed Get HTTP Request to HTTP Request, since it supports other methods too [Christina]
- Changed version formatting to 2022.X.X [LB2 dev team]
- Twitch Scam Train renamed to Twitch Hype Train [Christina]
- Get Twitch Connection command now accepts empty box for Account login name, which will default to the main Twitch account if left empty [Christina]
- Confirmation message for copying multiple commands [wolbee]
- Cleaner Trigger Pull Data dropdown [Sebas]
- Cleaner and additional OBS Triggers [Sebas]
- Due to Twitch Prediction outcomes changing from 2 to 10, the following has changed [Christina]:
	The old Twitch: Create Prediction command was renamed to Twitch: Create Prediction 2 Outcomes (all your previously made commands will still work)
	Added new Twitch: Create Prediction command that accepts an array of outcomes (max 10)
	Get Latest Poll/Prediction command can now retrieve Prediction Outcome 1-10 ID
	Trigger Pull Data command can now retrieve Outcome 1-10 Info
- Made commands that have default JSON code in text boxes taller so the code can be seen [wolbee]

###### UI Changes
- Changed the LB2 icon [LB2 dev team]
- Added default channel to the Channel label in the Twitch Chat Message command, to show which channel the message will be sent to if the channel name is left empty [Christina]
- Text/Label modifications, including clearer descriptions, spelling checks etc. [Christina]
- Changed input box names to better reflect what should be put into them: [Christinna]
	Save Variable As => save the result into a new or existing variable
	Added ms, s, db etc. to relevant boxes 
- Added donation, Discord and documentation buttons [Christina & wolbee]
- Changed copy command icon to the regular copy icon (originally scissors) [Silverlink]
- Changed move command icon to something more recognisable [wolbee]

###### Bug Fixes
- Fixed a bug that stopped you from resizing the text box and changing extension box color when sending extension commands from Transmitter [Christina]
- Fixed a bug with overlappable, non-persistent, non-queuable buttons not working if triggered with the Trigger Button command. [Christina] 
- Fixed a bug where the Command Line command would not show under Windows commands [Christina]
- Fixed a bug that defaulted Fetch OBS Data and Custom Packet to OBSws5 syntax [wolbee]
- Fixed YouTube crash for Member renewal events [Christina]
- Fixed clipboard clearing on LioranBoard start up (only works for text, images still get cleared) [Christina]
- Fixed Get Variable Type command returning undefined for any button variables (which are all objects) [Christina]
- Fixed ini files not properly getting .ini appended when the file name is 3 letters long [Christina]
