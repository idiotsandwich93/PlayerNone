PlayerNone

Story mode was never meant to feel empty. PlayerNone fixes that.

Originally a fork of the PlayerZero mod, PlayerNone has been rebuilt from the ground up into
something far beyond its origins — a full living session simulation that populates your story
mode world with AI characters modeled after GTA Online players. Not NPCs. Players. Named,
blipped, outfitted freemode characters with their own routines, rivalries, and agendas.

================================================================
What it does
================================================================

PlayerNone spawns a configurable session of AI "players" around you at all times. They drive,
walk, hang out at hotspots, browse shops, do ambient activities, and react to the world around
them — just like a real online lobby, minus the modders. Some will be friendly and want to team
up. Others will be hostile and come looking for you. Most are just living their lives.

Every character is generated with a randomized freemode appearance — civilian clothing, no police
gear, no masks — and assigned a name that appears on your map as a blip. They feel like real
session members because they're built to behave like them.

================================================================
Features
================================================================

- Dynamic session population — 5 to 50 AI players spawning and despawning naturally around you,
  configurable in the settings menu
- Dual-map support — fully functional in both Los Santos and Liberty City (requires LCPP)
- Behavioral AI — peds wander, drive, shop, run scenarios, hang out at LSR hotspots, and make
  decisions based on their personality type
- Friendly and hostile players — some want to ride with you, others want to kill you; aggression
  is configurable
- Gang system — criminal peds with gang affiliations, drug dealing, carjacking, and
  territory-aware behavior
- Economy layer — money drops, bounties, drug transactions between peds
- Vehicle AI — players drive on roads, pilot helicopters, fly planes; all map-aware with proper
  road snapping per region
- Contact system — AI players can appear in your in-game phone as contacts
- LSR integration — full compatibility with LosSantosRED; AI players pass LSR's converse check
  and receive dialogue menus like ambient civilians
- LSPDFR compatible — works alongside LSPDFR without conflict
- LSR Online session display — top-left corner shows your session as "LSR Online" with a live
  player count
- Custom red UI — distinct in-game menu with red color scheme

================================================================
For the LSR Community
================================================================

LSR makes the world react. PlayerNone makes it feel populated.

If you've spent time in LosSantosRED, you know what it does to story mode — the economy breathes,
gangs have territory, civilians have lives. What's been missing is the chaos layer. The feeling
that you're not alone in the session. That there are other players out there, with their own
business, their own beef, and their own relationship to the world LSR built.

That's what PlayerNone adds.

-- The concept --

PlayerNone spawns a configurable lobby of AI freemode characters around you — named, blipped, and
outfitted like GTA Online players — and drops them into your LSR world as full participants. Not
ambient pedestrians. Not props. Characters that move through the same systems LSR already runs,
respond to the same economy, and populate the same streets your gang controls.

Your session counter in the top left stops saying "GTA Online." It says LSR Online. Because that's
what this is.

-- How it integrates with LSR --

Every AI player spawned by PlayerNone is recognized by LSR as a valid conversable character. They
pass LSR's CanConverse check automatically, which means your full LSR dialogue system works on them
— the same menus, the same interactions you'd get with LSR's own ambient population. They aren't
invisible to LSR. They're part of it.

On the criminal side, PlayerNone reads LSR's gang configuration directly. The DrugDealerPercentage
values from your Gangs.xml determine how many peds in a given area are flagged as dealers or
criminals. Those peds will actively seek out drug transactions — including buying from LSR gang
members — making your gang territories feel genuinely active rather than decorative. Criminal peds
carjack, fight, and operate within LSR's existing gang zone logic. They belong to the same world.

Friendly civilian peds fill the other half of the session — wandering, shopping, running scenarios,
hanging out at LSR hotspots. They blend into LSR's ambient population seamlessly because they're
built from the same freemode character base LSR uses, with randomized civilian outfits.

When LSR is detected, PlayerNone automatically switches into enhanced mode, deepening all of these
integrations. If LSR isn't present, it runs standalone — same behavior, without the LSR-specific
hooks.

-- What it adds to your LSR experience --

- Your streets feel like a public session — named players on the map, freemode outfits, blips,
  real activity
- Gang territories have actual population pressure — criminal peds operating within your LSR
  economy
- Drug dealing isn't one-sided — AI buyers approach your LSR gang dealers and complete transactions
- Civilian peds respond to and interact with LSR's world naturally, not as afterthoughts
- Fully configurable session size (5-50), aggression, and session type to match whatever kind of
  LSR server environment you're running
- Liberty City support for LCPP users — same system, same LSR integration, different map

In short: LSR gives the world rules. PlayerNone gives it people. Together it's the closest story
mode has ever felt to a real modded online session — except the server never crashes, the modders
are gone, and everything actually works.

================================================================
Installation
================================================================

Place the PlayerNone folder into your Grand Theft Auto V / scripts folder.
Place PlayerNone.asi into your Grand Theft Auto V root folder.

================================================================
Requirements
================================================================

- Microsoft .NET Framework 4.8
  https://dotnet.microsoft.com/download/dotnet-framework/net48
- Visual C++ Redistributable for Visual Studio 2019
  https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads
- Script Hook V
  http://www.dev-c.com/gtav/scripthookv/
- Community Script Hook V .NET Nightly
  https://github.com/scripthookvdotnet/scripthookvdotnet-nightly/releases
- NativeUI
  https://github.com/Guad/NativeUI/releases
- iFruitAddon2
  https://github.com/Bob74/iFruitAddon2/releases

Optional:
- LosSantosRED (for enhanced mode)
- LCPP (for Liberty City support)

================================================================
Change Log
================================================================

---- Fork Changes by idiotsandwich93 ----


-- v61 - v65: Spawn Stability, Combat Overhaul, Weaponized Vehicle Purge --

Spawn / map detection
- Added explicit Liberty City file marker. PlayerNone/LibertyCity.txt must
  exist for the mod to switch into LCPP mode. isLC detection in
  FindPedSpPoint, FindVehSpPoint, and RandomLocation now requires both
  the marker file AND player X > 2800. Eliminates the long-standing
  "playerz spawn in and immediately die" loop caused by LS players
  flying over the eastern ocean (X > 2800) being misidentified as in
  Liberty City and given LC spawn coordinates while LCPP is not loaded.
- ZeroLC marker is auto-removed at mod startup, matching the existing
  ZeroYank (Yankton) and ZeroCayo (Cayo Perico) pattern. Map switcher
  mods should recreate the appropriate marker file each session.

Inter-gang combat and target picking
- ApplyGangRelationships now sets hostility between every pair of
  currently active gang groups, so rival gangs actually fight each
  other on sight. Gang vs Gp_Friend (civilians) was relaxed from
  hostile to neutral-ish (value 3) to stop ambient AI from killing
  random civilian peds the moment a gang member spawns nearby.
- FindAFight rewritten across all six sub-paths (plane main / plane
  fallback / heli main / heli fallback / on-foot aggression>9 / on-foot
  default) so peds in the same gang never target each other and rival
  gang members are picked as enemies even when both have Friendly=false.
  Previously only the on-foot default path had gang-aware targeting,
  which caused same-gang peds in helis or at max aggression to shoot
  each other and rival gang Players to ignore each other.

Easy-Way-Out (EWO) escape threshold
- Engaged peds previously set EnemyPos = (current distance) - 1.0f at
  the moment of contact, meaning any tiny movement away by the enemy
  would trip EWO and despawn them instantly. Changed to + 150.0f at
  four call sites in ProcessPZ — peds now only EWO when their target
  has truly retreated 150m beyond the original engagement distance.

Outfits, makeup, gang identity
- New ApplyGangColorProp function sets a hat prop (slot 0) in each
  gang's identity color so members are visually distinct on sight:
  Families green, Ballas purple, Vagos yellow, Marabunta blue, Aztecas
  teal, Diablos / Southside red. Diablos colors confirmed against LSR
  DispatchablePeople.xml; the rest are best-effort and easy to tweak.
- Male peds no longer get any face makeup (overlay forced to 255).
  Female peds limited to subtle makeup drawables 0-8 to stop face-paint
  drawables from appearing on civilians.
- Removed FemaleCatsuits from the female civilian outfit pool.
- Removed Hipster from the redneck gang outfit pool — overalls / muscle
  shirts / trucker via Standard + Casual now, no urban indie look.
- Added LC independent crews (Luca, McReary) to the organized-crime
  outfit bucket so they wear High Life / VIP / Designer / Finance &
  Felony like the other LC families.
- OnlineDress component-3 (torso/arms) fallback when an outfit has no
  explicit value: changed from drawable 0 to drawable 15 (LSR's reset
  default — universal freemode base torso, bare arms, no gloves).
  Fixes another class of missing-arm / missing-glove combos on certain
  jacket pairings.

Weaponized vehicle purge
- Removed every Arena War / Future Shock / Apocalypse / Nightmare
  weaponized variant from the standard road vehicle pool: ZR380 (all
  three variants), Dominator5/6, Impaler3/4, Imperator2/3, Slamvan5/6,
  Cerberus 1-3, Bruiser 1-3, Brutus 1-3, Sasquatch (Monster3/4/5),
  Issi 4/5/6, Deathbike 1-3, Dune3 (FAV), Dune4/5 (Ramp Buggy),
  Slamtruck, Hotring. None of these belong on civilian / gang peds
  driving around story mode.
- Removed weaponized bombers from the no-weapons plane pool: Alkonost,
  Volatol, Bombushka.
- Removed the entire WeaponisedRoadVehicles.ini list (vicList 6) and
  its in-menu entry from the favourite-vehicle picker. The remaining
  weaponized vehicles users can still pick are limited to Limo2 and
  Nightshark only (set in v11).
- Cleaned matching blip definitions for the removed bombers.

Keybind disable (v61, by request from Captain Vice)
- Setting Keys_Open_Menu, Keys_Clear_Session, or Keys_Invite_Only to
  -1 (or 0) in PzSettings.ini now fully disables that keybind instead
  of being silently overwritten with the default. Validation logic in
  FindSettings updated to honor the disabled state.
- Added "Disable Keyboard Binds" toggle in the in-game keybinds menu —
  flips all three keybinds between disabled (-1) and the original
  defaults (Z / X / C) in one click.
- WHileKeyDown short-circuits and returns false immediately when the
  key index is negative, so disabled binds never poll input.


-- v60: UI Polish --

- In-game menu color scheme changed from blue to red. Banner and inactive
  item backgrounds are now red; selected item highlight changed from yellow
  to white.
- Session label in the top-left corner changed from "GTA Online (Public, X)"
  to "LSR Online (Public, X)" to better reflect the mod's integration with
  Los Santos RED.
- Fixed player count description in PlayerNone Settings showing "5 - 30"
  instead of "5 - 50". The English.txt translation file was overriding the
  correct source string with stale text.


-- v59: Rename to PlayerNone --

- Mod renamed from PlayerZero++ to PlayerNone.
- ASI output renamed from PlayerZero++.asi to PlayerNone.asi.
- Scripts data folder path updated from PlayerZero/ to PlayerNone/ — rename
  your existing scripts/PlayerZero/ folder to scripts/PlayerNone/ on install.
- In-game menu title and settings label updated to reflect new name.
- Project files (.sln, .vcxproj) renamed and updated accordingly.
- Also includes spawn-node snapping for near-player ped spawns in LS/LC
  (prevents peds landing in water or off-terrain) and improved arm mesh
  fallback in OnlineDress (comp3 always applied after comp11, defaults to
  drawable 0 when outfit has no explicit torso value).


-- v58: Utility Belt Fix + Missing Arms Fix + Optimization Prep --

- Utility belts (component 9) now correctly zeroed for ALL peds, not just
  Friendly/Follower peds. Previously hostile and gang peds could still spawn
  with a tactical vest or utility belt visible.
- Fixed a second utility belt leak: gang peds that are re-dressed via
  SET_PED_DEFAULT_COMPONENT_VARIATION + OnlineDress had comp9 reset to the
  model default. An explicit comp9=0 call is now added after every gang
  re-dress to close this path.
- Fixed missing arms on some outfit combinations. OnlineDress now re-applies
  component 3 (torso/arms) after component 11 (jacket) so GTA V selects the
  correct arm mesh for the active jacket — applying comp3 before comp11 in
  the loop caused invisible arms on certain outfit pairings.
- FIB suit outfits removed from the Outfits folder rotation so FBI-style
  badge jackets no longer appear on any ped.
- Added DistanceToSq() helpers (squared-distance variants) in PZClass for
  use in hot comparison loops, avoiding unnecessary sqrt calls.


-- v57: Remove RentaCop Ped Type --

- Removed the RentaCop special ped, which had a ~5% chance of spawning a
  friendly ped in an LSPD uniform driving a police5 vehicle. Police uniforms,
  accessories, and vehicles are not part of the intended mod experience.
- Removed RentoCop global bool, spawn block in PlayerZerosAI, cleanup block
  in PedCleaning, and the RentaCop field from PlayerBrain.


-- v56: Remove Transit System --

- Removed the subway/transit system added in v52-v55. On-foot peds could not
  reliably navigate to underground station platforms via GTA V's pathfinder;
  they would walk to the entrance and stop. The feature was not achievable
  without map-level pathfinding hooks not available via Script Hook V.
- Removed: GoToTransit(), Phase 1 and Phase 2 transit handlers in ProcessPZ,
  LSSubwayStations and LCSubwayStations arrays, and the OnTransit,
  TransitTimer, and TransitStation fields from PlayerBrain.
- PickNextAction roll distribution restored to pre-transit behavior:
  1-50 wander, 51-70 shop, 71-80 scenario, 81-100 LSR hotspot.


-- v55: Transit — Fix ped not boarding at station entrance --

- Moved transit Phase 1 (proximity/hide) and Phase 2 (ride timer/teleport)
  checks to the top level of ProcessPZ, before the follower/friendly/driver
  chain. Previously those checks were buried inside the friendly/driver branch
  and never reached when any outer condition didn't match, leaving peds
  standing at the entrance indefinitely.
- Added alpha-restore guard: while a ped is hidden on the subway
  (OnTransit && TransitTimer > 0), the per-tick alpha reset to 255 is
  skipped so it cannot fight SET_ENTITY_VISIBLE.
- Removed duplicate transit checks from the old buried location.


-- v54: Transit System — Station Entry/Exit --

- Peds now visibly walk to the station entrance before boarding.
- When a ped reaches within 15m of their departure station, they are
  hidden (simulating entering the subway) and a ride timer (45-120s)
  starts. After the timer they reappear at a random station on the
  same map.
- Added TransitStation field to PlayerBrain to track which departure
  station the ped is heading to. Transit is now a two-phase process:
  walking (TransitTimer==0) then riding (TransitTimer>0).
- Fixed a bug where the ride timer started immediately at spawn time
  instead of when the ped actually reached the station.


-- v53: Complete Hacker Menu Removal --

- Completed the hacker menu removal started in v51. The Pz_TrollMenu
  function and its main-menu entry point were still present in script.cpp,
  causing the hacker menu ("hAcKErZZZ mENu") to appear in-game.
- Removed Pz_TrollMenu() and its entry in Pz_MenuStart(). The main menu
  now contains only: Contact Menu, Player Zero Settings, Clear Session,
  Invite, and Menu Orientation.
- Removed all subordinate hacker functions that were only reachable via
  the hacker menu: Pz_TrollPlayerz, Pz_TrollPed, Pz_TrollAdd,
  BurnPlayers, CashFlow, GetingOffHere, SnowTime (hacker-menu snow
  toggle), and HaCK001 through HaCK012.
- Removed EclipsWindMill, WindMill prop, and GotWindMill bool (Eclipse
  apartment windmill prop that was a hacker menu option).
- Removed LeaveYourApp helper (only called from Pz_TrollAdd).
- Replaced residual hacker-labeled strings in PZLangEng (PZSys.h) with
  neutral text so no hacker content can leak through any future string
  lookup. String indices are preserved (no removals) so all other
  PZTranslate[] references remain valid.
- NotWanted bool and its game-loop check at line 7292 are retained
  (now permanently false, harmless dead guard).


-- v52: Transit System (Subway / Train Stations) --

- On-foot peds now occasionally use the subway network (10% chance per
  PickNextAction roll). When selected, GoToTransit() walks the ped to
  the nearest station on the current map, then after 90 seconds to 3
  minutes (simulating the walk to the platform and the ride), teleports
  the ped to a random station on the same map so they emerge elsewhere.
- 30 subway stations sourced directly from Locations.xml and
  Locations_LPP.xml:
    LS (6 stations): Burton, Little Seoul, Del Perro, Portola Drive,
    LSIA Terminal 4, LSIA Parking.
    LC (24 stations): Hove Beach, Castle Garden, City Hall, Easton,
    East Park, Emerald, Feldspar, Frankfort Ave, Frankfort High,
    Frankfort Low, Hematite, Manganese East/West, North Park, Quartz
    St East/West, Suffolk, Vauxite, Vespucci Circus, West Park,
    Huntington St, Lynch St, San Quentin Ave, Winmill St.
- Map isolation enforced: LC peds always transit between LC stations;
  LS peds always transit between LS stations. The isLC (X>2800) check
  is evaluated at both dispatch and arrival.
- New PlayerBrain fields: OnTransit (bool) and TransitTimer (int).
  Transit timer handled in ProcessPZ alongside existing ShopTimer and
  ScenarioTimer checks. No existing behavior paths are affected.


-- v51: Remove Hacker Players and Hacker Menu --

- Removed the hacker player system entirely. This includes the random
  trigger that would secretly spawn a "DoomSlayer" AFK entry and convert
  it into a hostile cat-model ped with the TheHacker flag, the hacking
  sequence that teleported all peds to the windmill and dropped objects,
  the ProcessAfk hacker state machine (StartTheHack / HackingTime /
  HackSwitch / HackerIsInSession), and the FireOrb combat behavior used
  only by hacker peds.
- Removed Pz_HackedMenu and all GotHacked001-006 functions. The hacked
  menu replaced the normal in-game menu with a fake binary-string UI
  and applied annoying effects (language change, tree attachment, snow,
  player teleport, fire, wanted level). The normal menu now always opens
  without any HackAttacks check.
- Removed HackReaction flag usage from friend interaction callbacks.
  HackReaction had a 30% chance of despawning the reacting ped — no
  longer triggered since no hacker peds exist to cause it.
- GP_Mental relationship group declaration is kept (harmless) since it
  is referenced in group relationship setup code that would require a
  larger refactor to remove safely.


-- v50: Revert Map-Transition Bulk Despawn --

- Removed the v48 map-transition cleanup that set TimeOn=0 on all peds
  whenever the LC/LS map flag changed. The cleanup was too aggressive:
  any brief fluctuation in PlayerPosi() (cutscenes, interior loads, etc.)
  would flip the flag and instantly despawn every ped and driver. The
  existing per-spawn guards in FindPedSpPoint() (isLC coordinate check +
  hard sanity fallback) already prevent peds from spawning on the wrong
  map, making the bulk sweep unnecessary.


-- v49: Fix LC Driver Navigation + Map-Transition Guard --

- Fixed LC (LPP) driver navigation. RandomLocation() previously negated
  the player's X/Y to find a distant destination (valid LS logic: player
  at X=-500 gives V3P X=+500 which selects a different LS region).
  In LC the player is at X~5000, so negation produced X~-5000 which
  selected an LS VehDrops array. LC drivers were sent to LS coordinates,
  could not pathfind there, and stopped driving / went AFK. Fix: LC path
  picks a random SanLoocIndex entry from the five LC boroughs (16-20)
  and calls VehPlace() with that centre so drivers always get a valid
  LC-side destination. LS path is unchanged.
- Added player-entity existence guard to the v48 map-transition cleanup
  (PlayerZerosAI). If the player entity is not loaded (coords 0,0,0
  during a loading screen or cutscene), the cleanup check is skipped.
  Prevents a spurious LC->LS transition flip from incorrectly despawning
  all peds when the engine briefly returns an invalid position.


-- v48: Fix Map-Transition Ped Death Loop --

- Root cause of random ped deaths: the v41 fix prevented NEW peds from
  spawning at the wrong map's named locations, but peds already alive at
  LC named-location coordinates (X>2800) were never cleaned up when the
  player transitioned to LS. Those peds remained at LC world coordinates
  which are open ocean in the LS world-space, causing them to drown and
  respawn in a continuous loop.
- Added map-transition detection in PlayerZerosAI(). A static bool
  tracks whether the player was last seen in LC or LS. When the map
  changes (curIsLC != prevIsLC), all peds have TimeOn set to 0, queuing
  a clean despawn. ProcessPZ removes each ped normally and respawns it
  at a correct named location for the new map on the next cycle.
- No new static cache for map state — the static only records the
  previous state to detect changes; the current state is always read
  fresh from PlayerPosi() each tick.


-- v47: Road-Snap Restricted to Ground Vehicles Only --

- Fixed a bug in v46 where road-snap ran on every vehicle type,
  including aircraft (prefVeh 3/5/8/9, spawned 1200m up) and watercraft
  (prefVeh 2/4). The snap was pulling aircraft spawn positions down to
  the nearest road node, breaking aerial spawns.
- Road-snap now only runs in the ground-vehicle branch (VehPlace path),
  which covers LS and LC standard car/truck/bike spawns. Aircraft,
  boats, Yankton, and Cayo paths are unaffected.
- LC ground vehicles: road position + heading from nav node (unchanged).
- LS ground vehicles: road position only, VehPlace() heading preserved.


-- v46: LS Vehicle Road-Snap Restored (Position Only) --

- Road-snap (GET_CLOSEST_VEHICLE_NODE_WITH_HEADING) is now applied in
  both LC and LS to prevent vehicles spawning on rooftops, overpasses,
  or other undriveable geometry.
- For LC the road heading is also applied (unchanged from v39/v43).
- For LS only the position is moved to the nearest road node; the
  original VehPlace() heading is kept. This prevents the wrong-way
  drives and broken AI tasks that occurred when the snap also
  overwrote the LS heading.


-- v45: Spawn Radius Reverted to Safe Distances --

- Reverted near-player InAreaOf spawn radius from (50m, 100m) back to
  (30m, 60m) across all map branches (LS/LC, Yankton, Cayo).
  InAreaOf only offsets X/Y from the player position while keeping the
  same Z value. At 100m the terrain can be a cliff, rooftop, bridge, or
  open water, causing peds to spawn mid-air or in the ocean and die.
  The 30-60m range keeps spawns close enough that ground level is
  consistent with the player's Z.
- Narrowed nearCount detection radius from 100m back to 80m to match
  the 60m max spawn radius.
- Near-player cap remains at 4 (as set in v43).


-- v44: Remove Unsafe Pathfinder Call from Ped Spawning --

- Removed GET_SAFE_COORD_FOR_PED call that was added post-v41.
  This pathfinder call searched up to ~100m for any safe pedestrian
  position and could silently move a validated spawn coordinate across
  the X=2800 map boundary, bypassing all existing map guards and
  sending peds into the wrong-map ocean. The fix restores exact v41
  spawn finalization behavior.


-- v43: Ped Cap Raised to 4, Road-Snap Restricted to LC --

- Near-player ped cap raised from <2 to <4. Allows up to 3 on-foot peds
  within 100m before switching to location-based spawns across all maps.
- Vehicle road-snap (GET_CLOSEST_VEHICLE_NODE_WITH_HEADING) is now only
  applied when the player is in Liberty City (X > 2800). LS vehicles
  from VehPlace() are already on valid road positions; running the snap
  there was landing spawns on parking nodes and giving wrong headings,
  causing LS drivers to crash into traffic, drive on sidewalks, and lose
  their drive task entirely. LC retains the snap as LPP VehDrop
  coordinates can include rooftops and overpass geometry.


-- v42: Near-Player Ped Cap Fix + LC Interior Business Entry --

- Reduced near-player on-foot ped cap from <6 to <2 peds within 100m.
  Previously up to 5 peds could spawn within 80m and then walk toward
  the player, causing visible crowd clustering.
- Increased near-player spawn radius from 30-60m to 50-100m so peds
  start further away. Applied to LS/LC, Yankton, and Cayo branches.
- LSRData.cpp LoadLocations() now captures the <InteriorID> field from
  every location block and stores it in LSRLocation.interiorID. Previously
  this field was always -1, meaning no ped ever entered a business interior.
- LPP Init block now also calls LoadInteriors(Interiors_LPP.xml) so LC
  interior properties (weapon restriction, etc.) are resolved correctly
  for BurgerShot, Cluckin Bell, bars, and all other LC businesses.
- MAX_ROUTE_DIST for shop routing increased from 250m to 400m. LC
  businesses can be more spread out than LS, so the larger radius
  ensures peds always find a valid Bar/Restaurant/GasStation destination.


-- v40: XML Ped Spawn Rescan + Map Isolation Fix --

- Replaced both LCPedLocSpawns and LSPedLocSpawns arrays with coordinates parsed directly
  from the LSR XML files instead of the previous hand-estimated placeholders.
- LCPedLocSpawns now contains 258 real entries sourced from Locations_LPP.xml
  PossiblePedSpawns blocks where StateID is Liberty or Alderney. Covers all five boroughs:
  Algonquin, Broker, Dukes, Bohan, and Alderney.
- LSPedLocSpawns now contains 307 real entries sourced from Locations.xml PossiblePedSpawns.
  Covers Los Santos city, Blaine County, Sandy Shores, Paleto Bay, and surrounding areas.
- Stray Acter Police Station entries with clearly wrong coordinates (X ≈ -990) are excluded
  from the LC set by the X > 2800 coordinate filter.
- s_isLC map detection threshold raised from 2500 to 2800 to avoid misidentifying far-east
  Blaine County positions as Liberty City, eliminating wrong-map ped spawning.


-- v39: Vehicle Road-Snap on Spawn --

- Added GET_CLOSEST_VEHICLE_NODE_WITH_HEADING call in FindVehSpPoint() immediately after
  the VehDrop position is selected. Snaps X/Y/Z to the nearest navmesh road node and
  replaces the stored heading with the actual road direction.
- Fixes vehicles spawning on rooftops, overpasses, and off-mesh geometry — particularly in
  Alderney where several VehDrops21 entries sit on elevated expressway geometry.
- Falls back to the raw VehDrop coordinate if no road node is found within range.
- Applies to all maps: LS, LC (all five boroughs), Yankton, and Cayo Perico.


-- v38: Named Location Foot-Spawn System --

- Distant on-foot player spawns (beyond the 6-ped near-player cap) now pick from named
  real-world locations instead of a generic region-center-based PedPlace() call.
- Added LCPedLocSpawns array — Liberty City named ped spawn coordinates covering all five
  boroughs sourced from Locations_LPP.xml PossiblePedSpawns.
- Added LSPedLocSpawns array — Los Santos named ped spawn coordinates sourced from
  Locations.xml PossiblePedSpawns.
- FindPedSpPoint() distant-spawn else-branch replaced: randomly selects from the appropriate
  map's array (LCPedLocSpawns when s_isLC, LSPedLocSpawns otherwise), tries up to 12
  candidates to find one with fewer than 3 nearby on-foot peds, then spawns directly at
  that location's coordinates including heading.
- Near-player spawns (within 80m, capped at 6) are unchanged and still use InAreaOf().


-- v37: Liberty City Vehicle Spawn Coordinates --

- Replaced all five Liberty City vehicle spawn arrays (VehDrops17–21) with real road
  positions extracted from Locations_LPP.xml PossibleVehicleSpawns.
- Previous arrays contained round-number estimated coordinates that placed vehicles on
  building rooftops, in parks, and in water — especially in Alderney.
- VehDrops17 (Algonquin): 35 entries on Algonquin road network.
- VehDrops18 (Broker): 28 entries covering Broker/southern LC roads.
- VehDrops19 (Dukes): 40 entries on the Dukes/Queens road network.
- VehDrops20 (Bohan): 35 entries covering the Bohan/Bronx area.
- VehDrops21 (Alderney): 37 entries on Alderney/New Jersey roads.
- All coordinates carry accurate Z elevation and heading values from the XML.


-- v36: LC Ped and Vehicle Spawn Region Routing --

- Extended SanLoocIndex with five Liberty City region centers (indices 16–20): Algonquin,
  Broker, Dukes, Bohan, and Alderney.
- VehPlace() and PedPlace() dispatch chains extended to cover indices 16–21 (VehDrops17–21
  and PedDrops17–21) so LC ped and driver spawns route to the correct borough instead of
  always falling through to the LS arrays.
- Added LC spawn arrays PedDrops17–21 with ped-safe coordinates for each borough.
- North Yankton and Cayo Perico region centers added at indices 21–22.


-- v35: Map-Aware Shop Routing --

- GetNearestLocationWithInterior() now filters LSR shop locations to within 3 km of the
  requesting ped before selecting the nearest, so LC peds are never routed to LS shops
  and LS peds are never routed to LC shops.
- Falls back to the absolute nearest location if no shop qualifies within the distance cap
  (prevents null returns in sparse areas).


-- v34: Map-Aware Apartment Routing --

- AFKPlayers apartment list split into an LS range and an LC range using kLCApartmentStart
  index. InABuilding() selects from the correct range based on whether the player is in
  LC (X > 2500) or LS, so idle peds park in apartments on the same map as the player.


-- v33: LC-Aware Hotspot Routing --

- PlayerHotspots extended with fifteen Liberty City hotspot positions covering all five
  boroughs: Star Junction and North Holland (Algonquin), Purgatory (Algonquin south),
  Hove Beach and Firefly Projects (Broker), Beachgate (Broker east), Willis and Steinway
  (Dukes), Meadow Hills (Dukes east), Industrial and Fortside (Bohan), Northern Gardens
  (Bohan north), and Alderney City, Acter, and Westdyke (Alderney).
- Ped wander targets, driver destination hotspots, and scenario roaming all filter to
  hotspots within 3 km of the acting ped or vehicle before selecting randomly, ensuring
  LC peds stay in Liberty City and LS peds stay in San Andreas during normal activity.
- Falls back to absolute nearest hotspot if none qualify within the distance cap.


-- v32: Liberty City Outfit Classification --

- Added Liberty City gang IDs to GetGangCloths() style buckets so LC freemode peds wear
  contextually appropriate outfits instead of always defaulting to street attire.
- LC Italian crime families (Sindacco, Forelli, Leone) added to org-crime bucket alongside
  the existing GTA V five-families — wear High Life, VIP, Designer, Finance & Felony outfits.
- Jewish mob and Russian mob (Petrovic) added to org-crime bucket.
- Yakuza and Korean mob added to org-crime bucket.
- Uptown Riders added to MC bucket — wear Biker / Motorcycle Club outfits.
- North Holland Hustlers, Spanish Lords, Yardies, Diablos fall through to the street bucket
  (Lowrider, Lowrider Classics, Street, Import-Export) as appropriate for street-level gangs.


-- v31: Liberty City Preservation Project (LPP) Support --

- LSRData::Init() now automatically detects and loads Liberty City Preservation Project data
  when _LPP XML files are present in plugins/LosSantosRED/.
- Loads six LPP files at startup and merges them into the same runtime maps as Los Santos data:
  GangTerritories_LPP.xml, Zones_LPP.xml, Gangs_LPP.xml, Locations_LPP.xml,
  DispatchablePeople_LPP.xml, DispatchableVehicles_LPP.xml.
- No runtime map-switching required — LC zone internal names (ACTER, BOHAN, ALGON, etc.) are
  distinct from LS names, so all existing lookups (GetGangForZone, GetEconomyForZone,
  IsNearGangDen, GetRandomGangPedModel, GetRandomGangVehicle) automatically return LC-specific
  data when the player is in Liberty City.
- Dynamic neighborhood aggression fully applies to LC zones using Zones_LPP.xml economy
  classifications (wealthy LC neighborhoods stay calm, poor/gang areas are dangerous).
- LC gangs — Sindacco, Leone Family, Gambetti, Petrovic, North Holland Hustlers, Yardies,
  Lost MC LC chapter, Angels of Death LC, Uptown Riders, Spanish Lords, Diablos, and more —
  spawn in their correct territories with correct ped models and vehicles.
- Gang den proximity override applies to LC dens loaded from Locations_LPP.xml — gang members
  stay hostile near their LC dens regardless of neighborhood wealth class.
- Diagnostic log entries written to PlayerZero/LoggerLight.txt confirming how many LC zones,
  gangs, economy zones, and gang dens were merged at startup.


-- v30: Gang Den Proximity Spawning + Driver Despawn Fix --

- Gang members now spawn hostile near their gang dens even when the den is located in a wealthy
  neighborhood. The zone economy re-roll that would otherwise make peds friendly in rich areas
  is skipped entirely when the spawn point is within 150m of a known gang den.
- Applies to both on-foot peds and vehicle drivers via separate den proximity checks in
  SpawnPed() and SpawnVehicle() before the zone economy re-roll runs.
- Added LSRData::IsNearGangDen() — queries GangDen entries from Locations.xml by 2D X/Y
  distance. Returns the owning gang's AssignedAssociationID so the spawned ped is also
  assigned to the correct gang ID when no gang was already set.
- Added gangID field to LSRLocation struct to store AssignedAssociationID for gang dens.
- Fixed driver despawn bug: the SpawnVehicle() zone economy re-roll was flipping hostile
  drivers back to friendly in wealthy zones after PlayerPedGen had already set them hostile
  for den proximity. Den proximity check now runs before the re-roll in both code paths.


-- v29: Civilian Outfit Filtering + Missing Arms Fix --

- Removed all heist outfits (MaleHeist*, FemaleHeist*, Cayo Perico Heist*) from the civilian
  outfit whitelist. Friendly/civilian peds no longer spawn in heist gear.
- Added Lowrider Classics category to the civilian outfit pool for both male and female peds.
- Post-dress cleanup block now runs for all friendly and follower peds immediately after
  OnlineDress() and OnlineFaces(): resets component 1 (mask) to 0, component 5 (bags/hip
  accessories) to 0, and component 9 (utility belt/body armor) to 0. Gang and hostile peds
  keep their full outfit including masks and utility belts.
- Removed face paint (head overlay 4) from civilian male peds via SET_PED_HEAD_OVERLAY.
- Fixed missing arms and hidden hair on freemode peds: OnlineDress() was passing -1 drawable
  values from outfit INI files (which use -1 for unused slots) directly to
  SET_PED_COMPONENT_VARIATION, which hides that body component entirely. Changed check from
  != -10 to >= 0 so all negative drawable values are skipped.


-- v28: Gang-Accurate Outfits, Ped Models, and Vehicles --

- Gang peds now wear outfit categories that match their real GTA Online DLC sections instead of
  random civilian clothing. Street gangs (Ballas, Vagos, Families, Marabunta, Aztecas) wear
  Lowrider, Lowrider Classics, Street, and Import-Export outfits. MC gangs (Lost MC, Angels of
  Death) wear Biker and Motorcycle Club outfits. Org crime (Gambetti, Pavano, Lupisella, Messina,
  Ancelotti, Armenian mob, Wei Cheng, Kkangpae, Madrazo) wear High Life, VIP, Designer, Finance
  & Felony, and Luxury outfits. Redneck gangs wear Standard, Casual, and Hipster outfits.
- Gang ped models are now sourced from LSR's DispatchablePeople.xml. Each gang's PersonnelID
  maps to a DispatchablePersonGroup, and a random ModelName from that group is used for spawning
  instead of a generic freemode ped. Falls back to freemode if no LSR data is available.
- Gang vehicles are now sourced from LSR's DispatchableVehicles.xml using the same group lookup
  pattern. Each gang's VehiclesID maps to a list of period-appropriate vehicle models.
- Civilian outfit whitelist updated: removed all police, security, park ranger, and heist
  prefixes so civilians only wear regular street clothing categories.


-- v27: Drug Buy System --

- Added DoBuyDrugs(): civilian PZ peds in poor/criminal areas will now walk up to gang member
  dealers and simulate purchasing drugs from them. Buyers first scan for PZ peds with
  IsDealer=true within 30m, then fall back to ambient LSR gang peds identified by relationship
  group hash (ActiveGangGroups).
- Drug type is drawn from LSRData::GetRandomIntoxicant(), which reads Itoxicants.xml at startup — various substances including Marijuana, Cocaine, Crack,
  Heroin, Meth, and more.
- Buy chance scales by zone: 12% in poor/gang areas, 10% for high-aggression peds (tier 3),
  4% in middle-class areas. 3 to 7 minute cooldown between purchase attempts per ped.
- Added DrugBuyTarget and DrugBuyTimer fields to PlayerBrain struct to track buyer state
  across ticks. Buyer walks to dealer, waits 12-22 seconds, then resumes normal behavior.
- Added LSRData::LoadIntoxicants() which parses both intoxicant XML files at startup and
  populates an internal list. GetRandomIntoxicant() returns a random entry from that list.
- Fixed LoadInteriors() not being called in LSRData::Init() — interior data now loads correctly.


-- v26: Zone Economy Spawns, Traffic Laws, Vendor Purchase, Spawn Fixes --

- Zone-based civilian/hostile spawn ratios using LSR's economy classification. Wealthy areas
  (Vinewood, Rockford Hills) re-roll to ~85% friendly civilians. Poor areas (Davis, Strawberry)
  re-roll to ~75% hostile/criminal peds. Middle-class zones use default odds.
- Friendly peds are now fully unarmed — GunningIt() is skipped entirely for friendlies.
  All peds spawn with weapons holstered using WEAPON_UNARMED + equipNow=false.
- Friendly peds flee danger: SET_PED_FLEE_ATTRIBUTES set to flee from nearby weapons and when
  injured. When a hostile ped within 60m starts shooting, friendlies call TASK_SMART_FLEE_PED.
- Police interactions: friendly peds surrender via TASK_HANDS_UP when the player is being
  arrested. Hostile peds with AggressionTier >= 3 attack the officer; lower tiers flee.
- Improved spawn positioning: GET_SAFE_COORD_FOR_PED now uses flag 16 (sidewalk preference)
  so peds no longer spawn standing in the middle of roads.
- Stuck vehicle recovery interval increased from 5s to 30s, preventing false positives for
  law-abiding friendly drivers stopped at red lights (which can take 8-15 seconds).
- Interior vendor purchase: peds entering shops now use GET_PED_NEARBY_PEDS to find ambient
  clerk peds within 9m and walk up to them via TASK_GO_TO_ENTITY to simulate purchasing.
  Falls back to a browse scenario animation if no clerk ped is found nearby.
- Traffic law compliance: friendly/civilian drivers use GTA's law-abiding drive style
  (1074528293) at 10-18 m/s. Hostile/gang drivers use reckless style (786603) at 22-40 m/s.
  Based on DrivingAgainstTraffic and DrivingOnPavement entries in LSR's Crimes.xml.


-- v24: Interior Entry + Traffic Stop Features --

- On-foot peds now route to LSR business entrances using GetNearestLocationWithInterior().
  State machine handles entry (holsters weapon if interior is weapon-restricted), waits inside
  30-90 seconds, then exits and resumes normal behavior.
- Driver peds roll traffic violations every 10 seconds: speeding above 28 m/s or a 3% random
  chance. On a violation, the ped parks via TASK_VEHICLE_PARK for 40-75 seconds before
  resuming normal drive/fight logic.
- Added LSRInterior struct, Interiors map, LoadInteriors(), GetInterior(), and
  GetNearestLocationWithInterior() to LSRData. Locations.xml is now parsed for InteriorID to
  link location entries to their interior data.
- Added InteriorEntryID, InsideInterior, IsPulledOver, PulloverTimer, and TrafficViolTimer
  fields to PlayerBrain struct.


-- v23: Store Robbery Sequence --

- Added DoStoreRobbery(): three-phase sequence driven by existing timers.
  Phase 1 — criminal walks to the nearest ConvenienceStore or LiquorStore
  within 200m (sourced from LSR's Locations.xml). Phase 2 — on arrival,
  equips their armed weapon and aims it forward using TASK_AIM_GUN_AT_COORD
  for 8-14 seconds (visually holds the clerk at gunpoint). Phase 3 — holsters
  weapon and flees via TASK_SMART_FLEE_COORD, IsWanted set for 45 seconds.
  Falls back gracefully to no-op if LSR is not installed or no store is nearby.
- Store robbery rolls as a crime action alongside carjack, fight, and deal.
  Long cooldown (4x the zone timer) so it does not fire too frequently.
- Added RobPhase field (0-3) to PlayerBrain to track robbery state across ticks.


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
  for PlayerNone NPCs is now handled entirely by Los Santos RED's built-in interaction system.
  Enable TaskMissionPeds in LSR's Settings.xml to allow LSR to assign zone-based drug menus
  to PlayerNone peds the same way it does for ambient civilians.


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
  PlayerNone NPCs pass LSR's CanConverse check and receive full dialogue menus.
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
  settings file so PlayerNone NPCs can be targeted and interacted with by the LSR dialogue system.


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
- Added PlayerNoneSettings.exe to setup PZSet.ini.
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
- Adopcalipt's Player Zero 
- Rockstar Games
- Los Santos Red made by Greskrendtregk
- Everyone else
