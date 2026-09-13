# WarPawns_TemplateScenario

This is a working standalone scenario template.

Use it as the starting point for your first custom scenario.

## Install

Copy this entire folder to:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario
```

The final path must be:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
```

Launch War Pawns, open `Mods`, and check that the template is `Valid`.

Then open:

```text
Singleplayer -> Custom Scenarios
```

and press `Play`.

## Files

```text
manifest.json                       tells the game this folder is a mod
scenarios/template_scenario.scenario the scenario data
localization/en.json                 visible text and audio keys
images/preview.png                   scenario preview image
images/popup_thumbnail.png           popup image used by the template
```

## First safe edits

After the template works in game, try these edits one at a time:

1. Change the visible title in `localization/en.json`.
2. Change starting resources in `scenarios/template_scenario.scenario`.
3. Move one enemy unit to another valid coordinate.
4. Change the win condition.
5. Add or edit a popup.

Useful guides:

- [../../START_HERE.md](../../START_HERE.md)
- [../../docs/02_creating_your_first_scenario.md](../../docs/02_creating_your_first_scenario.md)
- [../../docs/05_using_maps.md](../../docs/05_using_maps.md)
- [../../docs/TROUBLESHOOTING.md](../../docs/TROUBLESHOOTING.md)
