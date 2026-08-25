# WarPawns_TemplateScenario

This is a working standalone custom scenario template.

## Install

Copy this entire folder to:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario
```

The final path must be:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
```

Then launch War Pawns and open:

```text
Mods
```

Expected status:

```text
Valid
```

Play it from:

```text
Singleplayer -> Custom Scenarios -> Template Scenario -> Play
```

## Files

| File | Purpose |
| --- | --- |
| `manifest.json` | Tells the game this folder is a custom scenario mod |
| `scenarios/template_scenario.scenario` | Scenario setup: map, players, units, objectives, triggers, commands |
| `localization/en.json` | Visible names, objective text, popup text, and optional audio refs |
| `images/preview.png` | Mod/scenario preview image |
| `images/popup_thumbnail.png` | Example popup image |
| `audio/` | Optional audio files |

## First safe edits

After it works in game, try one change at a time:

1. Change the visible title in `localization/en.json`.
2. Change `startingResources` in `scenarios/template_scenario.scenario`.
3. Move the enemy officer to another valid coordinate.
4. Change popup text.
5. Change the win condition.

See:

```text
docs/02_creating_your_first_scenario.md
```

## Do not forget

- JSON does not support comments.
- `scenarioId` in `manifest.json` must match `scenarioId` in the `.scenario` file.
- `workshopId` should be empty for a new local mod.
- Use `payload`, not `key`, for JSON scenario actions.

