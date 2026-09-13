# Creating your first standalone scenario

Start from `templates/WarPawns_TemplateScenario`.

The safest workflow is:

```text
copy template -> run it unchanged -> edit one thing -> run again
```

## 1. Copy and rename the template folder

Copy:

```text
templates/WarPawns_TemplateScenario
```

to:

```text
Documents/War Pawns/Mods/MyFirstScenario
```

## 2. Open the main files

You will edit these files most often:

```text
MyFirstScenario/manifest.json
MyFirstScenario/scenarios/template_scenario.scenario
MyFirstScenario/localization/en.json
```

## 3. Rename the mod ID

Open `manifest.json`.

Change:

```json
"id": "template_scenario_mod"
```

to something unique:

```json
"id": "my_first_scenario"
```

Use lowercase letters, numbers, and underscores. Do not use spaces.

## 4. Rename the scenario ID

Open `scenarios/template_scenario.scenario`.

Change:

```json
"scenarioId": "template_scenario_mod.template_scenario"
```

to:

```json
"scenarioId": "my_first_scenario.main"
```

Then return to `manifest.json` and make sure `scenarioId` matches:

```json
"scenarioId": "my_first_scenario.main"
```

If these two IDs do not match, the mod can become invalid.

## 5. Change the visible title and description

Open `localization/en.json`.

Change the text values for your title and description keys.

The visible title comes from `titleKey` in `manifest.json`.

Example:

```json
{
  "key": "my_first_scenario.title",
  "path": "My First Scenario"
}
```

## 6. Choose a map

Every scenario needs a map.

For a first scenario, use a built-in map ID:

```json
"map": {
  "id": "afccd13f3a754d49aa010c63dc297084"
}
```

This is the Ardennes map.

Do not invent map IDs. If you use your own `.map` file, use `path` instead:

```json
"map": {
  "path": "maps/my_map.map"
}
```

Full map guide: [05_using_maps.md](05_using_maps.md)

Built-in map IDs: [reference/BUILT_IN_MAPS.md](reference/BUILT_IN_MAPS.md)

## 7. Change starting units

Starting units are usually in `initialUnits`.

Example unit:

```json
{
  "ownerPlayerId": 0,
  "unitDataId": 2,
  "position": { "x": 2, "y": -12, "z": 10 },
  "personnel": 1.0,
  "experience": 0
}
```

Important:

- `ownerPlayerId` must exist in `players`.
- `unitDataId` is the unit index for that player's nation.
- `position` must be a valid cube coordinate on the selected map.
- Cube coordinates usually follow `x + y + z = 0`.

Useful references:

- Units: [reference/UNITS.md](reference/UNITS.md)
- Coordinates: [reference/COORDINATES.md](reference/COORDINATES.md)
- Standard coordinates CSV: [reference/standard_map_coordinates.csv](reference/standard_map_coordinates.csv)

## 8. Test in game

Open War Pawns:

```text
Mods -> select your mod
```

Expected:

```text
Status: Valid
```

Then open:

```text
Singleplayer -> Custom Scenarios
```

If `Play` is disabled, open [TROUBLESHOOTING.md](TROUBLESHOOTING.md).

## 9. Make only one change at a time

Recommended first edits:

1. Change title and description.
2. Move one enemy unit to another valid coordinate.
3. Change player starting resources.
4. Change the win condition.
5. Add a popup.

Use [recipes](recipes/) for copy-paste examples.
