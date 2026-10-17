# Update notes

## 2026-10-17 reference update

Latest Unity configuration screenshots, with no changes to game code or sample `.scenario` files:

- Added traits **78–82**: `HeavyATGun`, `ATGun`, `QuickLearners`, `Quartermaster`, `ScavengerTrait`.
- Added unit action **35**: `ATGunStrike` (`Distant Attack Action`).
- Added `unitDataId: 21` to each documented nation's `UnitsConfig.Items`:
  - Germany (`nationId: 0`) → `Pak40_G`
  - USA (`nationId: 3`) → `M1ATGun`
  - USSR (`nationId: 1`) → `Zis3`
- Corrected **55–75** trait indices from the earlier Unity screenshots: the preceding reference was off by one in this range and duplicated `MovementBoostTrait`. The current screenshot confirms `MovementBoostGrantingTrait: 74` and `MovementBoostTrait: 75`.
- **Open verification:** current trait index **54** is not visible in any of the newer screenshots available here. The old reference listed `SabotageDebuffTrait: 54`, while the newer screenshot clearly assigns it to **55**. Index **54** is therefore marked `UNVERIFIED_IN_CURRENT_SCREENSHOTS` in `traits.csv` and documented as unverified in `TRAITS.md` rather than inventing the trait name. Please supply a Unity screenshot covering approximately indices 50–56 for a fully complete list.
- Updated Markdown tables, matching CSV files, references index, ID quick guide, and README links. Corrected relative reference links in the archived Markdown documentation; its contents, all templates, and the legacy DOCX were otherwise preserved.

## 2026-10-02 reference update

Updated repository reference files for the latest visible game data:

- Added new traits to the reference list: `Supplies` and `LightArmor`.
- Confirmed unit action list still ends at `MovementBoostAction` (`actionId: 34`) in the provided screenshot.
- Added new faction field artillery units at `unitDataId: 20`:
  - Germany: `FieldArtillery_G`
  - USA: `FieldArtillery_USA`
  - USSR: `FieldArtillery_USSR`
- Added `docs/reference/units.csv` for easier lookup.
- Improved beginner-facing guidance in `README.md`, `docs/06_using_ids.md`, and `docs/TROUBLESHOOTING.md`.

## Notes for maintainers

When the game data changes, update both the Markdown tables and their CSV copies:

- `docs/reference/TRAITS.md` and `docs/reference/traits.csv`
- `docs/reference/UNIT_ACTIONS.md` and `docs/reference/unit_actions.csv`
- `docs/reference/UNITS.md` and `docs/reference/units.csv`
