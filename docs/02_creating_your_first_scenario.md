# 02 — Creating your first scenario

Start from the working standalone template. Do not write a `.scenario` file from scratch for your first mod.

## Step 1 — Copy the template

Copy:

```text
templates/WarPawns_TemplateScenario
```

into:

```text
Documents/War Pawns/Mods/
```

Then rename the folder to something unique, for example:

```text
Documents/War Pawns/Mods/My_First_Scenario
```

## Step 2 — Rename the mod ID

Open:

```text
manifest.json
```

Change:

```json
"id": "template_standalone_scenario_mod"
```

to something unique:

```json
"id": "my_first_scenario_mod"
```

Also update the visible title/description keys if you want:

```json
"titleKey": "my_first_scenario_mod.title",
"descriptionKey": "my_first_scenario_mod.description"
```

## Step 3 — Rename the scenario ID

In `manifest.json`, change:

```json
"scenarioId": "template_standalone_scenario_mod.scenario_01"
```

to:

```json
"scenarioId": "my_first_scenario_mod.scenario_01"
```

Now open:

```text
scenarios/template_scenario.scenario
```

Change the same field there:

```json
"scenarioId": "my_first_scenario_mod.scenario_01"
```

The `scenarioId` in `manifest.json` and the `.scenario` file must match.

## Step 4 — Update visible text

Open:

```text
localization/en.json
```

Add or update the text keys used by the manifest:

```json
{
  "key": "my_first_scenario_mod.title",
  "path": "My First Scenario"
},
{
  "key": "my_first_scenario_mod.description",
  "path": "A simple custom scenario for War Pawns."
}
```

The game shows text through localization keys. If a key is missing, the UI may show the raw key.

## Step 5 — Test before changing gameplay

Launch War Pawns.

Open:

```text
Mods
```

Expected status:

```text
Valid
```

Then open:

```text
Singleplayer -> Custom Scenarios
```

The scenario should appear with your new title.

## Step 6 — Make one safe gameplay edit

Good first edits:

- change `startingResources`
- move the enemy officer to another valid coordinate
- change popup text in `localization/en.json`
- change the highlighted zone

Example: change player starting resources:

```json
"startingResources": 10
```

Test again after each change.

## Step 7 — Use recipes for common logic

Useful next steps:

- [Win when all enemies are destroyed](recipes/win_when_enemies_destroyed.md)
- [Spawn reinforcements](recipes/spawn_reinforcements.md)
- [Trigger a popup when a unit enters a zone](recipes/trigger_popup_when_unit_enters_zone.md)
- [Give or take resources](recipes/give_or_take_resources.md)

