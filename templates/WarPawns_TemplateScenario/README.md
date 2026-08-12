# War Pawns Template Scenario

Copy this folder into `Documents/War Pawns/Mods/` and rename the folder, manifest id, scenario id, and localization keys.

Useful files:

- `manifest.json` - mod metadata and playable entry.
- `scenarios/template_scenario.scenario` - scenario setup and logic.
- `localization/en.json` - text and audio references.
- `images/preview.png` - mod/scenario preview image.
- `images/popup_thumbnail.png` - example custom popup thumbnail.

For campaign-unlock tests, do not add a new debug command. Temporarily replace the scenario `winConditionGroups` with a simple condition such as `RoundAtLeast` 1 and remove it before publishing.
