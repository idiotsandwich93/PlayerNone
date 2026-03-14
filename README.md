Player Zero++

Player zero brings all the toxic waste from online sessions and dumps it into story mode...

Features
- Collect bountys.
- Team up with playerz.
- Spawn kill playerz.
- Be spawn killed by playerz.
- Ride in playerz vehicles.

There is a settings ini where you can set max players, agression, wait times and play duration.

I have altered how outfits are generated if you wish to use custom outfits then you can with the wardrobe from NSPM yacht.

================================================================
Installation
================================================================

Place the scripts folder in the zip file in your Grand Theft Auto V folder.

================================================================
Required Files
-- Always check these are up-to-date as they do change. --
================================================================

The PlayerZeroSettings.exe requires the PriceDown Font.
https://fontmeme.com/fonts/pricedown-font/

All the free DLC's installed...
- Microsoft .NET Framework 4.8
  https://dotnet.microsoft.com/download/dotnet-framework/net48
- Visual C++ Redistributable for Visual Studio 2019
  https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads
- Script Hook V
  http://www.dev-c.com/gtav/scripthookv/
- Community Script Hook V .NET v2.10.14 or higher
  https://github.com/crosire/scripthookvdotnet
- NativeUI
  https://github.com/Guad/NativeUI/releases
- iFruitAddon2
  https://github.com/Bob74/iFruitAddon2/releases

This mod uses all the vehicles available, these require an up-to-date trainer so they don't despawn.
Any of these will work:
- Simple Trainer: https://www.gta5-mods.com/scripts/simple-trainer-for-gtav
- Menyoo: https://github.com/MAFINS/MenyooSP
- Enhanced Native Trainer: https://www.gta5-mods.com/scripts/enhanced-native-trainer-zemanez-and-others
- Add-On Vehicle Spawner: https://www.gta5-mods.com/scripts/add-on-vehicle-spawner

================================================================
Known Bugs and Compatibility Issues
================================================================

- Spawn kills (fix by lowering aggression).

================================================================
Future Updates
================================================================

...

================================================================
Change Log
================================================================

---- Fork Changes by idiotsandwich93 ----


-- v22: Visible Criminal Behavior — Armed Peds, Fights, Zone Aggression --

- Criminal peds now spawn with weapons that match their zone's gang profile
  (long guns, sidearms, or melee from Gangs.xml percentages) but with the
  weapon holstered — no draw animation fires on spawn, no wanted level generated.
  Weapon is only equipped when a crime action actually triggers.
- Added zone aggression tiers. Tier 3 (Davis, Strawberry, Rancho, Skid Row,
  Banning, Elysian Island) — frequent carjacks, fights, and dealing. Tier 1
  (Vinewood, Rockford Hills, Beverly Hills, Golf Club) — rare events. Everything
  else is tier 2. Tier drives both crime frequency and action probabilities.
- Added DoFight(): criminal ped equips their weapon and attacks the nearest
  ambient GTA pedestrian within 40m using TASK_COMBAT_PED. LSR's passive crime
  detection picks this up as a game-native assault event automatically.
- Crime timer is now zone-scaled: tier 3 = 30-60s between attempts, tier 2 =
  60-120s, tier 1 = 120-240s. Davis feels like Davis; Vinewood stays quiet.
- Carjack and fight thresholds scale by tier: high-crime areas roll 30% carjack
  and 40% fight chance per crime tick; low-crime areas roll 10% and 5%.
- Post-crime wanted flee: after a carjack or fight, IsWanted is set and the ped
  flees (TASK_SMART_FLEE_COORD) for 45-60 seconds, then holsters their weapon
  and returns to normal ambient behavior.
- LSR location routing now filters to within 250m of the ped's position.
  Peds no longer get routed to destinations 2km away that they would despawn
  before reaching. Falls back to wander if nothing close enough is found.
- Added AggressionTier and ArmedWeaponHash fields to PlayerBrain struct.
- Fixed: LSR detection notification now fires 8 seconds after load, when the
  player is actually in control and will see it.


-- v21: LSR Data Integration — Zone-Aware NPC Simulation --

- Added LSRData module (LSRData.h / LSRData.cpp) that reads Los Santos RED's XML files at
  startup: GangTerritories.xml, Zones.xml, Gangs.xml, and Locations.xml. All data is loaded
  once and queried at runtime — no live dependency on LSR, no timing issues with Shift+F10.
- LSR is now an optional enhancement. If plugins/LosSantosRED/ is not found, the mod runs in
  standalone mode with all existing behavior unchanged. A startup notification confirms which
  mode is active.
- Zone-aware crime rates: spawned NPCs now check the GTA zone they appear in against LSR's
  GangTerritories.xml. If the zone belongs to a gang, that gang's FightPercentage and
  DrugDealerPercentage (from Gangs.xml) drive how many PZ peds in that area are criminal or
  dealing. Gang territory NPCs behave statistically like real LSR gang members.
- Economy-scaled crime in non-gang zones: areas classified as Poor (from Zones.xml) get higher
  crime rates (35% criminal / 40% dealer); Rich zones get much lower rates (8% / 10%); Middle
  zones stay at the v19 defaults.
- Time-of-day location routing via Locations.xml: PickNextAction() now routes NPCs to actual
  LSR-defined map locations based on the current in-game hour. Evening/night NPCs walk to bars;
  daytime NPCs head to restaurants or gas stations; dealer NPCs route to illicit marketplaces.
  Falls back gracefully to the static hotspot list when LSR is not present.
- Added GangID, ZoneEconomy, IsWanted, WantedTimer, and SchedulePhase fields to PlayerBrain
  struct to track per-NPC LSR state across ticks.
- GetGangGroupForZone() now reads live territory data from LSRData instead of the previous
  hardcoded map. The hardcoded map is kept as a fallback for standalone mode.


-- v20: Removed Custom Drug Buy Prompt --

- Removed the custom [E] Buy ($50) drug purchase prompt added in v19. Drug buying and selling
  for PlayerZero++ NPCs is now handled entirely by Los Santos RED's built-in interaction system.
  Enable TaskMissionPeds in LSR's Settings.xml to allow LSR to assign zone-based drug menus
  to PlayerZero++ peds the same way it does for ambient civilians.


-- v19: NPC Crime Behaviors + LSR Drug Interaction Groundwork --

- Added IsCriminal flag (20% of spawned NPCs) that gates crime behaviors behind a cooldown
  timer, so chaos is possible but not constant.
- Added IsDealer flag (25% of criminals, ~5% overall) that enables drug-dealing-related behavior
  in the crime system.
- Added carjacking behavior for criminal NPCs. Uses GTA V's native TASK_ENTER_VEHICLE with flag
  9, which plays the carjack animation and ejects the driver. Criminal NPCs roll a 20% chance
  each crime tick to attempt a carjack on the nearest unoccupied vehicle that isn't the player's.
  Cooldown of 3 to 6 minutes between attempts.
- Added NPC-to-NPC drug deal behavior for dealer NPCs. Dealer walks to the nearest on-foot NPC
  within 20 metres using TASK_GO_TO_ENTITY, simulating a street deal visually. Cooldown of 1 to
  2 minutes between attempts.
- Added CrimeTimer field to PlayerBrain struct to track per-NPC crime action cooldowns
  independently of the existing ShopTimer and ScenarioTimer fields.
- Replaced the near-player spawn percentage with an absolute cap: on-foot NPCs only spawn near
  the player if fewer than 5 on-foot NPCs are already within 80 metres, preventing overcrowding
  at any player count without being tied to the MaxPlayers setting.


-- v14: Scenario Timers + Richer NPC Behavior + Near-Player Spawns --

- Added a ScenarioTimer field to each NPC brain. Ambient scenarios now expire after 15 to 40
  seconds and the NPC automatically picks a new activity, instead of sitting frozen in an
  emote until the next AI tick fires.
- Added PickNextAction — a weighted action dispatcher that gives on-foot NPCs four possible
  activities: play an ambient scenario (35%), walk to a nearby shop or amenity (30%), walk to
  a map hotspot such as a bar, ATM, or corner store (20%), or wander to a random nearby point
  then settle into a new scenario (15%). Previously NPCs only had the scenario-or-shop split.
- Restored a small near-player spawn chance. 10% of on-foot NPC spawns now land within 30 to
  60 metres of the player so there is always some local activity. The remaining 90% continue
  to scatter across random map regions as introduced in v11.


-- v13: Los Santos RED Compatibility + Zone-Aware Gang Groups --

- Fixed the root cause of NPCs showing as "Talk to unknown" with no dialogue options in Los
  Santos RED. Changed AllowMissionPedsToInteract to true in the LSR Settings.xml so that
  PlayerZero++ NPCs pass LSR's CanConverse check and receive full dialogue menus.
- Added zone-aware gang group assignment. Hostile NPCs that spawn inside gang territory zones
  are now added to the matching GTA V ambient gang relationship group (AMBIENT_GANG_BALLAS,
  AMBIENT_GANG_LOST, AMBIENT_GANG_MARABUNTE, etc.) instead of the generic attack group.
  Because LSR reads relationship group names at runtime, it automatically classifies these
  NPCs as gang members with territory awareness, crime tracking, and police dispatch — no LSR
  source changes required.
- Removed SET_BLOCKING_OF_NON_TEMPORARY_EVENTS from idle and walking NPCs so LSR can trigger
  conversation animations and interactions on them. The flag is still set on combat, vehicle,
  aviation, and hacker NPCs where it is needed to prevent interruption.
- Added zone-based scenario pools in DoAmbientScenario. Street zones use urban scenarios,
  rural and highway zones use countryside scenarios, and remaining areas use a general pool,
  so NPC animations feel appropriate for where they are on the map.


-- v12: Blaine County Coverage + Player Count Increase --

- Added 23 Grapeseed pedestrian spawn points covering Grapeseed Ave, east farm roads, and the
  southern connector to Sandy Shores. Previously only 15 entries existed for this entire area.
- Added 26 Grapeseed vehicle road paths covering the full Grapeseed Ave north-south corridor,
  east farm grid, and Route 68 southern approach — increasing coverage from 10 to 36 entries.
- Added 31 north Blaine / Procopio pedestrian entries covering Route 1 west (Paleto to Procopio
  connector), Braddock Pass area, and additional Procopio Promenade positions — nearly doubling
  the previous list.
- Added 21 vehicle road entries covering Route 1 driving paths from Paleto Bay east all the way
  to the existing Procopio coverage, filling the dead zone between the two regions.
- Raised the max player count slider cap from 30 to 50. Updated the in-menu description to note
  that 30 or below is recommended for best performance. The cap is now a user choice rather than
  a hard limit.


-- v11: Map-Wide NPC Spawning + FiveM-Style Identity Overhaul --

- Rewrote the NPC spawn point system — on-foot NPCs now spawn in a randomly selected region from
  all 16 map regions instead of always clustering near the player. NPCs now scatter across the
  entire map like a real populated server, appearing in Sandy Shores, Grapeseed, Paleto, and
  rural Blaine County even when the player is in Los Santos.
- Vehicle spawning intentionally left unchanged — vehicles still spawn near the player for
  performance and gameplay reasons.
- Expanded name generation with FiveM / RP-server style gamertags. Added 70+ new name fragments
  across four categories: prefixes, core words, numeric suffixes, and postfixes. Generated names
  now read like real online gamertags (e.g. xSniper99, DarkReaperYT, LilGhostGG).
- Renamed all 7 pre-built contact files from phonetic-syllable placeholders to FiveM-style
  gamertags:
    Deeea175    ->  GhostXx
    Eeyie       ->  DrifterGG
    Goy         ->  BlazeTV
    Louay       ->  xSniper99
    Nireai258   ->  RavenPro
    Pir         ->  ReaperXx
    Zaiore454   ->  ShadowYT
- Removed 40+ unrealistic vehicles from the vehicle list: arena war variants, military vehicles,
  futuristic/flying cars (Deluxo, Oppressor mk1/mk2 road variants, Scramjet, Vigilante, etc.),
  monster truck variants, and duplicate entries. Kept all standard sports cars, muscle cars,
  sedans, SUVs, vans, motorcycles, and utility trucks.
- Reduced the weaponised vehicle list from 18 entries to 2 (Limo2 and Nightshark only). Removed
  the Insurgent variants, Caracara, Menacer, Technical variants, Scarab variants, APC, Halftrack,
  Riot2, Rhino, and Khanjali.
- Removed the Halloween Arena War outfit — NPCs no longer spawn in space-horror costumes during
  Halloween and instead use the regular online outfit system.
- Fixed Los Santos RED compatibility — changed AllowMissionPedsToInteract to true in the LSR
  settings file so PlayerZero++ NPCs can be targeted and interacted with by the LSR dialogue system.


-- v9 / v10: Shop AFK Fix + T-Pose Fix --

- Fixed shop AFK: NPCs now leave shops after 20 to 45 seconds and receive a new ambient task,
  instead of standing idle indefinitely once they walk into a store.
- Fixed t-poses: removed 5 scenario strings that caused the NPC to freeze in a T-pose.
  Retained 10 confirmed-safe idle animation strings.


-- v8: AFK Spawn Fix --

- Added a random ambient idle system that picks from 10 safe animations (smoking, phone, leaning,
  drinking, etc.) to give on-foot NPCs a visible activity.
- Fixed AFK spawning: all on-foot NPCs now immediately receive a task on spawn — either a random
  idle animation or a walk to a nearby location (50/50 chance). Previously they would stand still
  indefinitely after spawning.
- Same idle-forcing logic applied inside the AI tick loop so on-foot NPCs that finish a task
  don't go AFK mid-session either.
- Added helper functions for cleaner follower task assignment and NPC-vs-NPC combat assignment.
- Walk destination function now accepts both coordinate types so callers don't need to manually
  convert them.


-- v3 to v7: Relationship, Aggression & Snow System Rework --

- Added passive mode handling that sets all NPC group relationships to neutral, ensuring NPCs
  stop firing at the player without needing to clear all tasks.
- Reworked the relationship system with aggression-scaled values instead of hardcoded maximums.
  At low aggression settings (3 or below), NPCs dislike each other rather than outright hating
  each other, which reduces how quickly fights escalate. Hostile player relationships now only
  kick in above aggression 5 instead of aggression 4.
- Relationship assignments now validate that they were actually applied and retry if not,
  preventing silent failures on session start.
- Removed the inline snow toggle from the main script file. Snow is now handled externally via
  V_Functions.asi, so the snow system works independently of the main script.


-- v2: Code Architecture & Cleanup --

- Removed global namespace import to avoid naming conflicts throughout the codebase.
- Removed unused source files that were left over from earlier development.
- Added a separate menu source file for cleaner code organisation.
- Removed several dead functions that were no longer called anywhere in the mod.
- Simplified the outfit directory reader, settings loader, and language loader to reduce
  boilerplate in the rest of the codebase.


================================================================

Original Source: https://github.com/Adopcalipt/Player_Zero

================================================================
Original Changelog
================================================================

Version 1.91
- Fixed no reaction to player aggression when on foot near player.
- Fixed RNG to run more efficiently.
- Fixed reset remove assets to run more efficiently.
- Fixed bountys disappearing.
- Fixed settings exe not registering changes to radar and notify settings.
- Fixed an enter friendly vehicle fault.
- Added option to remove contacts via menu.
- Added more ped varieties and removed the outfit.xml.

Version 1.9
- Save your friends and call them into session anytime.
- Rebalanced the aggression levels.
- Re-worked the Players AI for a greater variety of actions.
- More vehicle peds including helis and planes.
- Enter players vehicles via mod menu... Even the ones that dont like you!
- Ride the Sandy to LSA flight.
- Added remove radar by request.
- Added remove notifications by request.
- Fixed the orbital cannon death loop.

Version 1.81
- Coz there is always something missed.....
- Fixed Orbital Cannon, spawn kill fault if aggression set to 11.
- Fixed null ref oppressor attack.

Version 1.8
- Added a Mod Menu. Kick players, drop objects etc.
- Can now set the settings ingame from the menu.
- Added the updated vehicles.

Version 1.7
- Added an invite friendly player on foot option.
- Added PlayerZeroSettings.exe to setup PZSet.ini.
- Attempted to fix the peds falling through the map fault.

Version 1.6
- Moved the find peds/vehicles/seats to ontick.
- Added the Mk2 Oppressor to the air attack mode (available on aggression of 7 or above).
- Added more blip variety by finding specific vehicle blips.

Version 1.5
- Altered following ped relationships, on low aggression you can't harm your followers.
- Altered the following positions to behind the player.
- Fixed a fault with respawning peds not matching the peds that died.
- Altered how the controls are used — two keys are now required for clearing out and toggling
  off the mod to prevent accidental triggering.

Version 1.42
- Optimised the player AI for less fps drop.
- Made the logfile optional and removed a faulty rewrite system.

Version 1.41
- Fixed infinite loop fault when a dead ped tried to resurrect multiple times.

Version 1.4
- Added disable mod option.
- Added set accuracy option to settings.
- Added random off radar for players.

Version 1.3
- Fixed followers entering vehicles when you are out of vehicles.
- Fixed followers manually entering vehicles too far from their current location.
- Added max followers of 7.
- Set the following blips to blue.
- Added Hackerz. To access the hackerz set aggression to 11.
- Fixed a null ref error if outfits.XML is missing.
- Fixed any undeclared public Lists (may have caused some OutOfRange fails).

Version 1.2
- Altered how aggression is handled.
  If less than 2 the players won't turn aggressive.
  If less than 4 no aggressive players will spawn but will require provocation.
  If greater than 9 then all players are aggressive.
- Fixed invisible players.
- Added following players to use their own vehicles if no seat is free.
- Added more online blips, specific to vehicles (plane, heli, car).
- Changed the default clear session key.

Version 1.1
- Updated blip changes and slow to open player list.
- Option to alter keys.
- Option to have space weapons.
- Option to clear session.
- Fixed excess driver aggression for low aggression setting.
- Added planes.
- Added no planes or helis on low aggression.
- Added orbital strike that randomly fires if you spawn kill a ped too many times with
  aggression set above 7.

Version 1.0
- First release.

================================================================
Credits
================================================================

- Rockstar Games
- FedoraScrub (Tank Mech): https://www.gta5-mods.com/vehicles/tank-mech-menyoo
- Everyone else
