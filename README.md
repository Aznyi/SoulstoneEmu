# SoulstoneEmu
Issues tracker only for Soulstone Emu an AscentEmu based 2.4.3 emulator.


# Change Log Below


Revision: 21
Author: Aznyi
Date: Thursday, September 10, 2020 2:57:08 PM
Message:
* Implemented / Loaded Item.dbc which was missing from Ascent so we can utilize values from it in the code, this is the first step of adding additional missing DBCs to improve our blizzlike posture
* Changed Field108 to Sheath to match MaNGoS an SQL will be added soon for this change in the database side as well
----
Revision: 20
Author: Aznyi
Date: Thursday, September 10, 2020 2:25:26 PM
Message:
* Improvements on how we load the Spell.dbc spellfixes information so it is faster. We no longer need to perform an Open directly since it is already loaded on start up we should not load it again and again or have multiple instances of it loading
----
Revision: 19
Author: Aznyi
Date: Thursday, September 10, 2020 2:24:37 PM
Message:
* More Ascent -> MaNGoS items table columns

RequiredRanks are not labeled properly to be RequiredHonorRank, RequiredCityRank
RequiredSkillSubRank is now RequiredSpell
RequiredReputation is now RequiredReputationFaction and RequiredReputationRank

This lays out the columns for a better understanding as previously they were just Rank1, Rank2, Unk etc.

----
Revision: 18
Author: Aznyi
Date: Thursday, September 10, 2020 1:48:23 PM
Message:
* Change ItemPrototype packet structure and database structure to match MaNGoS more. This corrects fields we have in the database labeled as "unk" to give them proper SocketContent column names.
* Moved older world sql fixes to an additional folder
----
Revision: 17
Author: Aznyi
Date: Thursday, September 10, 2020 1:16:48 PM
Message:
* Adding Duration to update packet structure for SMSG_ITEM_QUERY_SINGLE_RESPONSE for 2.4.2 that was missing. Credits to MaNGoS for the proper name and information.
----
Revision: 16
Author: Aznyi
Date: Wednesday, September 9, 2020 9:15:56 PM
Message:
* Changed .recall to .teleport and adjusted the sub commands as well per Olan's request

Example:
.recall port -> .teleport to
.recall port player -> .teleport player
.recall port add-> .teleport add

----
Revision: 15
Author: Aznyi
Date: Wednesday, September 9, 2020 5:23:36 PM
Message:
* Adding custom .bank command for Olan, tested and working.
----
Revision: 14
Author: Aznyi
Date: Wednesday, September 9, 2020 2:15:26 PM
Message:
More Transport Work
* Corrected speed hacking detection
* Adjusted timing of period of travel so that you don't fall through the transport any longer
----
Revision: 13
Author: Aznyi
Date: Wednesday, September 9, 2020 12:35:19 PM
Message:
Re-wrote Transport system
* Transport times now load from core instead of database
* Transports now load from gameobject_names instead of transports_data
* Dropped transports_data table
* Changed how transport travel paths are loaded from the DBCs and correct how waypoints are generated which puts the transport on it's proper path
* Corrected teleporting the player and sending SMSG_TRANSFER_PENDING during the teleportation to present the proper loading screens during movement

TO-DO

Fix the Deeprun Tram as it is not present or spawned in world and investigate how it is handled from a core perspective.
Correct speed hacking on transports to not disconnect, possibly do a GOBJ Select and check if it is near and disable speed hacking if so? Other cores just seem to add delays to theirs but this seems easy to bypass.

----
Revision: 12
Author: Aznyi
Date: Tuesday, September 8, 2020 3:21:32 PM
Message:
[DB]:
* Rebased the entire database, the previous one was based on WhyDB however their final revision was honestly.. awful. This is NCDBs final version
* Cleaned up Changeset_1.txt removing the quest information but keeping UDBs start / finish tables
----
Revision: 11
Author: Aznyi
Date: Tuesday, September 8, 2020 2:33:46 PM
Message:
[DB]:
* Converted Quest tables from UDB to Ascent for all quest templates and for the start and stop assigned NPCs

This fixes the first noticed issue.. when going into game you couldn't do any starting quests at all now you can.

----
Revision: 10
Author: Aznyi
Date: Tuesday, September 8, 2020 1:59:20 PM
Message:
* Resolving a few more 2.4.3 login issues
* Removed AD extractor and left the compiled version

----
Revision: 9
Author: Aznyi
Date: Monday, September 7, 2020 9:03:57 PM
Message:
* Name correction for compiling

----
Revision: 8
Author: Aznyi
Date: Monday, September 7, 2020 8:59:33 PM
Message:
* Updated Spell.dbc format for 2.4.3
* Updated login capability to version 2.4.3 of World of Warcraft, Credits to the Wcell / MaNGoS teams for the encryption method discovery

----
Revision: 7
Author: Aznyi
Date: Monday, September 7, 2020 8:39:44 PM
Message:
* Extracted 2.4.3 client UpdateFields and updated our sources

TO-DO

Review how MaNGoS handles 2.4.3 and implement it.

----
Revision: 6
Author: Aznyi
Date: Monday, September 7, 2020 6:49:05 PM
Message:
* updated min / max build for TBC 2.4.3 only and removed settings from config files
----
Revision: 5
Author: Aznyi
Date: Monday, September 7, 2020 6:39:17 PM
Message:
* World now compiles
* hash_map to unordered_map
* New coding standards requires proper spacing for built in variables.. so this caused roughly 300 compile errors which have now been corrected

TO-DO

Fix 260 compile warnings..

----
Revision: 4
Author: Aznyi
Date: Monday, September 7, 2020 5:52:53 PM
Message:
* Logonserver now compiles more hash_map cleanup

TO-DO:

Correct laundry list of warnings regarding uninitialized variables

----
Revision: 3
Author: Aznyi
Date: Monday, September 7, 2020 5:13:33 PM
Message:
+ Added base Ascent libraries
* Removed revision extraction for now to compile in shared project
* Updated StackWalker to the latest version this corrects a majority of compiling issues with VS2019
* hash_map & hash_set are depreciated we have moved this to unordered_map & unordered_set correcting multiple compiling issues
* Corrected compiling issue in CrashHandler.cpp after updating StackWalker

----
Revision: 2
Author: Aznyi
Date: Monday, September 7, 2020 4:37:37 PM
Message:
* VS 2008 -> VS 2019
- Removed VoiceChat and RealmServer we will not be using these or developing these moving forward
+ Added initial first Changeset file and running log for items fixed on the database side compared to WoW Classic for TBC

TO-DO:

Correct compiling, update source code to latest standards.


