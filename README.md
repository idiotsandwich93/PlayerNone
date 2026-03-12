<u> Player Zero++ </u>

Player zero brings all the toxic waste from online sessions and dumps it into story mode...
Features
	-Collect bountys.
	-Team up with playerz.
	-Spawn kill playerz.
	-Be spawn killed by playerz.
	-ride in playerz vehicles.

There is a settings ini where you can set max players, agression, wait times and play duration.

I have altered how outfits are generated if you wish to use custom outfits then you can with the wardrobe from NSPM yacht.

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
<b>installation</b>
==*==*==*==*==*==*==*==

Place the scripts folder in the zip file in your 'Grand Theft Auto V' folder.

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
<b>Required Files</b>
--Always check these are up-to-date as they do change.--
==*==*==*==*==*==*==*==
The PlayerZeroSettings.exe requires the <a href="https://fontmeme.com/fonts/pricedown-font/">PriceDown Font</a>.

All the free DLC's installed...
	<a href="https://dotnet.microsoft.com/download/dotnet-framework/net48">Microsoft .NET Framework 4.8 </a>
	<a href="https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads">Visual C++ Redistributable for Visual Studio 2019 </a>
	<a href="http://www.dev-c.com/gtav/scripthookv/">Script Hook V</a>
	<a href="https://github.com/crosire/scripthookvdotnet">Community Script Hook V .NET v2.10.14 or higher</a>
	<a href="https://github.com/Guad/NativeUI/releases">NativeUI</a>
	<a href="https://github.com/Bob74/iFruitAddon2/releases">iFruitAddon2</a>

This mod uses all the vehicles avalable, these require an uptodate trainer so they don't despawn.
Any of these will work.
	<a href="https://www.gta5-mods.com/scripts/simple-trainer-for-gtav">Simple-Trainer</a>
	<a href="https://github.com/MAFINS/MenyooSP">Menyoo</a>
	<a href="https://www.gta5-mods.com/scripts/enhanced-native-trainer-zemanez-and-others">Enhanced-Native-Trainer</a>
	<a href="https://www.gta5-mods.com/scripts/add-on-vehicle-spawner">Add-On Vehicle Spawner</a>

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
<b>Known Bugs and Compatibility Issues</b>
==*==*==*==*==*==*==*==

- spawn kills (fix by lowering aggression).

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
<b>Future updates</b>
==*==*==*==*==*==*==*==
...
==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
<b>Change Log</b>
==*==*==*==*==*==*==*==

<u>Fork Changes — idiotsandwich93</u>
<ul>

    <b>-- v12: Blaine County Coverage + Player Count Increase --</b>
    <li>Added 23 Grapeseed pedestrian spawn points (<code>PedDrops14</code>) covering Grapeseed Ave, east farm roads, and the southern connector to Sandy Shores. Previously only 15 entries existed for this entire area.</li>
    <li>Added 26 Grapeseed vehicle road paths (<code>VehDrops14</code>) covering the full Grapeseed Ave north-south corridor, east farm grid, and Route 68 southern approach — increasing coverage from 10 to 36 entries.</li>
    <li>Added 31 north Blaine / Procopio pedestrian entries (<code>PedDrops16</code>) covering Route 1 west (Paleto → Procopio connector), Braddock Pass area, and additional Procopio Promenade positions — nearly doubling the previous 33-entry list.</li>
    <li>Added 21 vehicle road entries to <code>VehDrops16</code> covering Route 1 driving paths from Paleto Bay east all the way to the existing Procopio coverage, filling the dead zone between the two regions.</li>
    <li>Raised max player count slider cap from <b>30 → 50</b>. Updated in-menu description to note 30 or below is recommended for best performance. The cap is now a user choice rather than a hard limit.</li>

    <b>-- v11: Map-Wide NPC Spawning + FiveM-Style Identity Overhaul --</b>
    <li>Rewrote <code>FindPedSpPoint()</code> — on-foot NPCs now spawn in a randomly selected region from all 16 <code>SanLoocIndex</code> map regions instead of always clustering 30–60 units from the player. NPCs now scatter across the entire map like a real populated server, appearing in Sandy Shores, Grapeseed, Paleto, and rural Blaine County even when the player is in Los Santos.</li>
    <li>Vehicle spawning intentionally left unchanged — vehicles still spawn near the player for performance and gameplay reasons.</li>
    <li>Fixed <code>Vector4</code> default constructor build error in <code>PZSys.cpp</code> introduced by the spawn rewrite (<code>Vector4 Pos;</code> → <code>Vector4 Pos(0.0f, 0.0f, 0.0f, 0.0f);</code>).</li>
    <li>Expanded name generation word banks in <code>PZSys.h</code> with FiveM/RP-server style gamertags. Added 70+ new name fragments across four lists: prefixes (<code>sListOpeniLet</code>), core words (<code>sListVowls</code>), numeric suffixes (<code>sListPadding</code>), and postfixes (<code>sListPostfix</code>). Generated names now read like real online gamertags (e.g. <code>xSniper99</code>, <code>DarkReaperYT</code>, <code>LilGhostGG</code>).</li>
    <li>Renamed all 7 pre-built contact <code>.ini</code> files from phonetic-syllable placeholders to FiveM-style gamertags:
        <ul>
            <li>Deeea175 → GhostXx</li>
            <li>Eeyie → DrifterGG</li>
            <li>Goy → BlazeTV</li>
            <li>Louay → xSniper99</li>
            <li>Nireai258 → RavenPro</li>
            <li>Pir → ReaperXx</li>
            <li>Zaiore454 → ShadowYT</li>
        </ul>
    </li>
    <li>Updated all <code>PlayersName</code> and <code>PlayersId</code> fields inside each contact file to match the new names.</li>
    <li>Removed <b>40+ unrealistic vehicles</b> from <code>StandardRoadVehicles.ini</code>: SCRAMJET, VIGILANTE, DELUXO, STROMBERG, TOREADOR, VOLTIC2, BRICKADE, SLAMTRUCK, WASTLNDR, MARSHALL, BRUISER/BRUTUS/MONSTER series, ZR380 variants, arena war DOMINATOR/IMPALER/IMPERATOR/SLAMVAN variants, RUINER2/4, ZHABA, WINKY, CERBERUS series, DEATHBIKE series, SANCTUS, SHOTARO, and duplicate entries. Kept all standard sports cars, muscle cars, sedans, SUVs, vans, motorcycles, and utility trucks.</li>
    <li>Reduced <code>WeaponisedRoadVehicles.ini</code> from 18 entries to 2 (LIMO2 and NIGHTSHARK only). Removed INSURGENT variants, CARACARA, MENACER, TECHNICAL variants, SCARAB variants, APC, HALFTRACK, RIOT2, RHINO, and KHANJALI.</li>
    <li>Removed the Halloween Arena War outfit block — the <code>else if (ItHalloween)</code> branch applying <code>MaleArenaWarSpace_Horror</code> / <code>FemaleArenaWarSpace_Horror</code> outfits was deleted. NPCs now fall through to regular <code>OnlineDress()</code> during Halloween instead of wearing space-horror costumes.</li>
    <li>Fixed Los Santos RED compatibility — changed <code>AllowMissionPedsToInteract</code> from <code>false</code> to <code>true</code> in the LSR <code>Settings.xml</code> so PlayerZero++ NPCs can be interacted with by the LSR dialogue system.</li>

    <b>-- v9 / v10: Shop AFK Fix + T-Pose Fix --</b>
    <li>Fixed shop AFK (v9): added <code>ShopTimer</code> field to <code>PlayerBrain</code> — NPCs now leave shops after 20–45 seconds and receive a new ambient task, instead of standing idle indefinitely once they walk into a store.</li>
    <li>Fixed t-poses (v9): removed 5 scenario strings from <code>DoAmbientScenario()</code> that caused the NPC to freeze in a T-pose: <code>MOBILE_FILM_SHOCKING</code>, <code>AA_COFFEE</code>, <code>MUSCLE_FLEX</code>, <code>CHEERING</code>, <code>TOURIST_MAP</code>. Retained 10 confirmed-safe scenario strings.</li>

    <b>-- v8: AFK Spawn Fix --</b>
    <li>Added <code>DoAmbientScenario()</code> — picks randomly from 10 confirmed safe idle animations (smoking, phone, leaning, drinking, etc.) to give on-foot NPCs a visible activity.</li>
    <li>Fixed AFK spawning: all non-driver, non-passenger, non-follower NPCs now immediately receive a task on spawn — either a random ambient scenario or a <code>WalkHere()</code> to a nearby shop or location (50/50 chance). Previously they would stand still indefinitely after spawning.</li>
    <li>Same idle-forcing logic applied inside the AI tick loop so on-foot NPCs that finish a task don't go AFK mid-session.</li>
    <li>Added <code>FollowPed()</code> helper for cleaner follower task assignment.</li>
    <li>Added <code>GreefWar()</code> for NPC-vs-NPC combat task assignment.</li>
    <li>Overloaded <code>WalkHere()</code> to accept both <code>Vector3</code> and <code>Vector4</code> so callers don't need to manually unpack coordinates.</li>

    <b>-- v3–v7: Relationship, Aggression & Snow System Rework --</b>
    <li>Added <code>PassiveDontShoot()</code> — sets all NPC group relationships to neutral (0) for passive mode, ensuring NPCs stop firing at the player without needing to clear all tasks.</li>
    <li>Reworked <code>SetRelationType()</code> with aggression-scaled relationship values instead of hardcoded maximums:
        <ul>
            <li>Attack↔Friend and Attack↔Mental relationships now use value 3 (dislike) when aggression ≤ 3, and 5 (hate) at higher settings — previously always 5.</li>
            <li>Friend↔Player hostile relationships (value 2) now only applied when aggression > 5 — previously triggered at aggression > 4, causing unwanted aggression at moderate settings.</li>
        </ul>
    </li>
    <li><code>SetRelationType()</code> now validates that relationships were actually applied and retries if not, preventing silent failures on session start.</li>
    <li>Removed inline <code>EnableSnow()</code> from script.cpp — snow toggling is now handled externally via <code>V_Functions.asi</code>.</li>
    <li>Added <code>AccessSnowFallType()</code> and <code>AccessLetItSnowType()</code> — dynamically load and call snow functions from <code>V_Functions.asi</code> at runtime, so the snow system works independently of the main script.</li>

    <b>-- v2: Code Architecture & Cleanup --</b>
    <li>Removed global <code>using namespace std</code> — all standard library types now use explicit <code>std::</code> prefix to avoid naming conflicts.</li>
    <li>Corrected namespace casing: <code>PZclass</code> → <code>PZClass</code> throughout.</li>
    <li>Removed unused source files: <code>Materials.h</code>, <code>Win32Native.cpp</code>, <code>Win32Native.h</code>.</li>
    <li>Added <code>GtaVMenu.cpp</code> and <code>GtaVMenu.h</code> for cleaner menu system separation.</li>
    <li>Improved function signatures — <code>AddRelationship()</code> and <code>AddGraphics()</code> now take <code>const std::string&</code> instead of by-value <code>string</code>.</li>
    <li>Removed dead code: <code>NotTheSame()</code>, <code>LaggOut()</code>, <code>LandingGear()</code>, <code>LandNearPlane()</code>, <code>BuildFlightPath()</code>.</li>
    <li>Outfit directory reading simplified — replaced manual <code>filesystem::directory_iterator</code> loop with <code>ReadDirectory()</code> helper.</li>
    <li><code>FindSettings()</code> API simplified — time calculations moved inside the function, callers no longer need to compute them manually.</li>
    <li><code>LoadLang()</code> now accepts the language setting as a parameter (<code>MySettings.Pz_Lang</code>) instead of reading it internally each call.</li>

</ul>

<u>Version 1.91</u>
<ul>
    <li>Fixed no reaction to player aggression when on foot near player.</li>
    <li>Fixed RNG to run more efficently.</li>
    <li>Fixed reset remove assets to run more efficently.</li>
    <li>Fixed bountys dissapearing.</li>
    <li>Fixed settings exe not regestering canges to radar and notify settings.</li>
    <li>Fixed an enter friendly vehicle fault.</li>
    <li>Added option to remove contacts via menu.</li>
    <li>Added more ped variaties removed and the outfit.xml.</li>

</ul>

<u>Version 1.9</u>
<ul>
    <li>Save your friends and call them into session anytime</li>
    <li>Rebalanced the agression levels.</li>
    <li>Re-worked the Players Ai for a greater varity of actions.</li>
    <li>More vehicle peds including heilies and planes.</li>
    <li>Enter players vehicles via mod menu... Even the ones that dont like you!!.</li>
    <li>Ride the Sandy to LSA flight.</li>
    <li>Added remove radar by request.</li>
    <li>Added remove notifications by request.</li>
    <li>Fixed the orbital cannon death loop.</li>

</ul>

<u>Version 1.81</u>
<ul>
    <li>Coz there is always someting missed.....</li>
    <li>Fixed Orbital Cannon, spawn kill fault if aggression set to 11.</li>
    <li>Fixed null ref oppressor attack.</li>

</ul>

<u>Version 1.8</u>
<ul>
    <li>Added a Mod Menu. kick players, drop objects etc.</li>
    <li>Can now set the settings ingame from the menu.</li>
    <li>Added the updated vehicles.</li>

</ul>

<u>Version 1.7</u>
<ul>
    <li>Added a invite frendly player onfoot option.</li>
    <li>added PlayerZeroSettings.exe to setup PZSet.ini.</li>
    <li>atempted to fix the peds falling through the map fault.</li>

</ul>

<u>Version 1.6</u>
<ul>
    <li>Moved the find peds/vehicles/seats to ontick.</li>
    <li>Added the Mk2 Oppressor to the air attack mode (avalable on aggerssion of 7 or above).</li>
    <li>Added more blip variaty by finding specific vehicle blips.</li>

</ul>
<u>Version 1.5</u>
<ul>
    <li>Altered folllowing ped relationships, on low aggression you can't harm your followers.</li>
    <li>Altered the following postions to behind the player.</li>
    <li>Fix a fault with resporning peds not matching the peds that died.</li>
    <li>Altered how the controls are used now two keys are reqired for clearing Out and Toggling off the mod to prevent accidental triggering.</li>

</ul>

<u>Version 1.42</u>
<ul>
    <li>Optimised the player AI for less fps drop.</li>
    <li>Made the logfile optional and removed a faulty rewrite system.</li>

</ul>

<u>Version 1.41</u>
<ul>
    <li>Fixed infinate loop fault when a dead ped tryed to resurect multiple times.</li>

</ul>

<u>Version 1.4</u>
<ul>
    <li>Added disable mod option.</li>
    <li>Added set accuracy option to settings.</li>
    <li>Added random off radar for players.</li>

</ul>

<u>Version 1.3</u>
<ul>
    <li>Fixed followers entering vehicles when you are out of vehicles.</li>
    <li>Fixed followers manualy entering vehicles too far from there current location.</li>
    <li>Added max followers of 7.</li>
    <li>Set the following blips to blue.</li>
    <li>Added 'Hackerz'. To access the hackerz set agression to 11.</li>
    <li>Fixed a null ref error if outfits.XML is missing.</li>
    <li>Fixed any undeclared public Lists.(may have caused some OutOfRange fails)</li>

</ul>

<u>Version 1.2</u>
<ul>
    <li>Altered how aggression is handled.</li>
    <li>-If less than 2 the players wont turn aggressive.</li>
    <li>-If less than 4 no agressive players will spawn but will require provication.</li>
    <li>-If greater than 9 then all players are aggresive.</li>
    <li>Fixed invisable players.</li>
    <li>Added following players to use there own vehicles if no seat is free.</li>
    <li>Added more online blips, and specific to vehicles, i.e plane, heli, car</li>
    <li>Changed the default clear session key.</li>

</ul>

<u>Version 1.1</u>
<ul>
    <li>Updated blip changes and slow to open player list.</li>
    <li>Option to alter keys.</li>
    <li>Option to have space weapons.</li>
    <li>Option to clear session.</li>
    <li>fixed excess driver agression for low agression setting.</li>
    <li>Added planes.</li>
    <li>Added no planes helis on low aggresion.</li>
    <li>Added orbital strike randomly fires if you spawn kill a ped too many times with aggresion set above 7.</li>
</ul>

<u>Version 1.0</u>
<ul>
    <li>First release</li>
</ul>

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
<a href="https://github.com/Adopcalipt/Player_Zero">Original Source</a>
==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
<b>Credits</b>
==*==*==*==*==*==*==*==

--Rockstar Games
--FedoraScrub's https://www.gta5-mods.com/vehicles/tank-mech-menyoo
--Everyone else

==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==*==
