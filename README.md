# Zygor Guides Viewer Remaster for Conquest of Azeroth

[Zygor Guides Viewer Remaster](https://github.com/ErebusAres/ZygorGuidesRemaster-3.3.5a_WOTLK) (3.0.253, WotLK 3.3.5a) with changes that make it work on the **Conquest of Azeroth** (Ascension-based) client, plus a **CoA Talent Advisor** for the 21 CoA classes.

This is an unofficial compatibility fork. All credit for the viewer goes to the remaster project and the original Zygor authors.

## Install

1. Close the game.
2. Download this repository (Code → Download ZIP).
3. Copy the `ZygorGuidesViewerRM` folder into `<your client>\Interface\AddOns\`, replacing any existing copy.

If you use TomTom, use its CoA version as well (the `coa-tomtom` repository).

## What's changed for CoA

| Problem on CoA | Fix |
|---|---|
| ~50 extra maps (starting areas, caves, CoA zones) had no size data in Astrolabe, so the arrow had nothing to aim with | Map sizes taken from the client's own `WorldMapArea.dbc`; case-insensitive map names (`Libs/Astrolabe/AstrolabeCoAData.lua`) |
| The client's built-in `Astrolabe-0.4` numbers zones by area ID | Zygor's own Astrolabe copy also accepts an area ID |
| Starting areas and caves report as their own zone ("Northshire Valley" instead of "Elwynn Forest"), so "go to" steps never completed | They're folded into the parent zone (`CoAZones.lua`) |
| The route planner got CoA's native `C_Map` IDs | Positions come from Zygor's own map data (`LibRover-1.0.lua`, `MapCoords.lua`) |
| The Gear Advisor rejected all armor for CoA classes | CoA class specs (`Data-WOTLK/CoA-ClassSpecs.lua`); armor/weapon usability from the character's skills |
| Weapon DPS weights were erased for every class (upstream bug) | Fixed in `Item-ItemScore.lua` |
| 49 "Error loading" lines at startup | Empty placeholder entries dropped from the guide and build `Autoload.xml` files |

## CoA Talent Advisor

`ZygorTalentAdvisorCOA` adds leveling builds for all 21 CoA classes (70 specs):

- A panel beside the CoA talent window, with points/order numbers drawn on the talent trees.
- **Preview** another spec's tree without switching.
- **Load build** puts the build into the talent window as unsaved changes, trimmed to what your level and points allow. Nothing is learned until you click Apply.
- Its own "CoA Talent Advisor" tab in Zygor's options (panel opacity, open with the talent window, tree numbers, preview).
- `/ztacoa` for commands.

It only appears on Conquest of Azeroth characters.

## Credits

- **Zygor Guides Viewer Remaster:** [ErebusAres/ZygorGuidesRemaster-3.3.5a_WOTLK](https://github.com/ErebusAres/ZygorGuidesRemaster-3.3.5a_WOTLK), based on the classic Zygor Guides Viewer.
- **Talent builds:** [Ascension Sidekick](https://ascensionsidekick.com). We tried to reach the Sidekick team to ask for permission but couldn't find a working contact. If you're from Sidekick and want the build data removed or credited differently, please open an issue.
- **CoA class spec data:** from Kui_Nameplates' CoA class database.

## License

The viewer is distributed under the GPL designation of the upstream project; see [LICENSE](LICENSE) (the remaster's licensing notice, kept unchanged). Bundled libraries, guides, data and artwork keep their own licenses and copyrights.
