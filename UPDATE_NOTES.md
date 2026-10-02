# Update notes

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
