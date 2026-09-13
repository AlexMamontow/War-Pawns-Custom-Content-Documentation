# War Pawns custom content format reference

> New to War Pawns custom content? Start with [../START_HERE.md](../START_HERE.md). This file is the full technical reference, not the beginner walkthrough.


This is the full format reference for custom scenarios and campaigns. If you are new, start with [START_HERE.md](../START_HERE.md), then use the recipes in `docs/recipes/`.

---


This guide describes the v1 local/Workshop custom content format for War Pawns.

## Folder location

Local mods are placed here:

```text
Documents/War Pawns/Mods/
```

One local mod is one playable entry: either a standalone scenario or a campaign.

## Recommended repository layout

```text
README.md
docs/
  MODDING.md
  reference/
    BUILT_IN_MAPS.md
    COORDINATES.md
    ENUMS.md
    UNITS.md
    TRAITS.md
    SCENARIO_REFERENCE.md
    PAYLOADS.md
templates/
  WarPawns_TemplateScenario/
  WarPawns_TemplateCampaign/
```

## Mod folder layouts

Standalone scenario:

```text
WarPawns_MyScenario/
  manifest.json
  scenarios/my_scenario.scenario
  localization/en.json
  images/preview.png
  images/popup_thumbnail.png
  audio/
```

Campaign:

```text
WarPawns_MyCampaign/
  manifest.json
  campaigns/my_campaign.campaign
  scenarios/mission_01.scenario
  scenarios/mission_02.scenario
  localization/en.json
  images/preview.png
  images/popup_thumbnail.png
  audio/
```

## ID rules

Use globally unique IDs. Recommended pattern:

```text
mod id:        my_mod
scenario id:   my_mod.mission_01
campaign id:   my_mod.campaign
localization:  my_mod.popup.title
```

Do not reuse base scenario ids.

## Manifest

Standalone scenario manifest:

```json
{
  "formatVersion": 1,
  "id": "my_scenario_mod",
  "titleKey": "my_scenario_mod.title",
  "descriptionKey": "my_scenario_mod.description",
  "author": "Your Name",
  "version": "1.0.0",
  "gameVersion": "",
  "contentType": "Scenario",
  "scenarioId": "my_scenario_mod.scenario_01",
  "entry": "scenarios/my_scenario.scenario",
  "preview": "images/preview.png",
  "localization": [{ "language": "en", "path": "localization/en.json" }],
  "workshopId": ""
}
```

Campaign manifest:

```json
{
  "formatVersion": 1,
  "id": "my_campaign_mod",
  "titleKey": "my_campaign_mod.title",
  "descriptionKey": "my_campaign_mod.description",
  "author": "Your Name",
  "version": "1.0.0",
  "gameVersion": "",
  "contentType": "Campaign",
  "campaignId": "my_campaign_mod.campaign",
  "entry": "campaigns/my_campaign.campaign",
  "preview": "images/preview.png",
  "localization": [{ "language": "en", "path": "localization/en.json" }],
  "workshopId": ""
}
```

`gameVersion` may be empty. If it is set and differs from the current game version, the mod remains playable but the UI shows a warning.

`preview` is mod-relative and optional. Missing previews use the game's placeholder image.

## Localization

Localization files use arrays, not dictionaries:

```json
{
  "texts": [
    { "key": "my_mod.title", "path": "My Mod" },
    { "key": "my_mod.popup.title", "path": "Briefing" }
  ],
  "audio": [
    { "key": "my_mod.radio_01", "path": "audio/radio_01.ogg" }
  ]
}
```

Popup `audioKey` values reference keys from the `audio` array.

## Campaign file

```json
{
  "formatVersion": 1,
  "campaignId": "my_campaign_mod.campaign",
  "titleKey": "my_campaign.title",
  "descriptionKey": "my_campaign.description",
  "preview": "images/preview.png",
  "scenarios": [
    {
      "scenarioId": "my_campaign_mod.mission_01",
      "path": "scenarios/mission_01.scenario",
      "titleKey": "my_campaign.mission_01.title",
      "descriptionKey": "my_campaign.mission_01.description",
      "preview": "images/preview.png"
    },
    {
      "scenarioId": "my_campaign_mod.mission_02",
      "path": "scenarios/mission_02.scenario",
      "titleKey": "my_campaign.mission_02.title",
      "descriptionKey": "my_campaign.mission_02.description",
      "preview": "images/preview.png",
      "requiredScenarioIds": ["my_campaign_mod.mission_01"]
    }
  ]
}
```

A mission is unlocked when all `requiredScenarioIds` are completed in the same campaign.

## Scenario map selection

Use a base-game map id:

```json
"map": { "id": "afccd13f3a754d49aa010c63dc297084" }
```

Or a mod-relative map file path:

```json
"map": { "path": "maps/my_map.map" }
```

Use only one of `id` or `path`. See [Built-in map IDs](reference/BUILT_IN_MAPS.md) and [Coordinates](reference/COORDINATES.md).

## Scenario graph

A `.scenario` file contains setup data and a scenario graph:

```json
{
  "formatVersion": 1,
  "scenarioId": "my_mod.scenario_01",
  "titleKey": "my_mod.scenario.title",
  "map": { "id": "afccd13f3a754d49aa010c63dc297084" },
  "players": [],
  "initialUnits": [],
  "initialZones": [],
  "graph": {}
}
```

The graph contains steps and the main objective. Condition groups in win/lose objectives use OR between groups and AND inside each group.

## Available scenario logic

Full lists are in [Scenario reference](reference/SCENARIO_REFERENCE.md).

### Triggers

| Trigger | Description |
| --- | --- |
| ScenarioStarted | Fires when the scenario starts. |
| AnyEvent | Fires on any executed game command, not on scenario start. |
| TurnEnded | Fires after an end-turn command. |
| TurnStarted | Fires after an end-turn command; combine with CurrentPlayerIs/CurrentTeamIs. |
| RoundStarted | Fires when a new round starts. |
| ZoneCaptured | Fires after commands that may change zone ownership. |
| UnitAttacked | Fires after attack or scenario artillery strike. |
| UnitMoved | Fires after movement, adjacent move, or swap command. |
| UnitKilled | Fires when at least one unit changed from alive to dead after a command. |


### Conditions

| Condition | Description |
| --- | --- |
| AlwaysTrue | Always passes. |
| FlagTrue | Flag key exists. |
| FlagFalse | Flag key does not exist. |
| IntAtLeast | Counter key is at least intValue. |
| TeamControlsZones | teamId controls all listed zones. teamId -1 means any non-neutral team. |
| UnitsDead | All listed unitIds are dead. |
| AnyUnitMatches | At least one unit matches targets. |
| NoUnitsMatch | Zero units match targets. |
| UnitCountAtLeast | Matching unit count is at least intValue. |
| UnitCountAtMost | Matching unit count is at most intValue. |
| RoundAtLeast | Current round is at least intValue. |
| RoundEquals | Current round equals intValue. |
| CurrentPlayerIs | Current player is playerId or one of playerIds. |
| CurrentTeamIs | Current team is teamId or one of teamIds. |
| PlayerResourcesAtLeast | All selected players have at least intValue resources. |
| PlayerResourcesAtMost | All selected players have at most intValue resources. |
| TeamResourcesAtLeast | All selected teams have at least intValue total resources. |
| TeamResourcesAtMost | All selected teams have at most intValue total resources. |


### Actions

| Action | Description |
| --- | --- |
| ShowUnitMessagePopup | Shows UnitMessagePopup. Supports pages with title/body/audioKey/thumbnail. |
| ShowRegularPopup | Shows regular popup. |
| ShowTutorialPopup | Shows tutorial-style popup. |
| ShowNarrationPopup | Shows narration popup. |
| HighlightZone | Highlights relatedZones. |
| ClearHighlightZone | Clears highlighted zones. |
| SetFlag | Sets scenario flag from payload. |
| AddCounter | Adds to counter key; use intValue. |
| SendCommand | Runs commandId with payload. |
| EndMission | Ends the mission. Include win in payload for completion/progress. |


### Commands

| commandId | Description |
| --- | --- |
| promote_player_officer | Promote officer through payload. |
| update_recruitable_units | Replace available recruitable units. |
| spawn_units | Spawn units; occupied spawn hex falls back to nearest available map hex. |
| update_units | Patch explicit units or selector-selected units. |
| update_players | Patch player resources/control/spawn areas. |
| give_resources | Add/subtract resources; amount may be negative. |
| modify_unit_traits | Add/remove/replace traits on selector-selected units. |
| unlock_steam_achievement | Unlock Steam achievement by API name. |


## Unit target selector

```json
"targets": {
  "allUnits": true,
  "aliveOnly": true,
  "unitIds": [10, 11],
  "ownerPlayerIds": [0],
  "teamIds": [1],
  "nationIds": [0],
  "unitDataIds": [2],
  "unitTypes": ["Infantry", "Tank"],
  "hexes": [{ "x": 0, "y": 0, "z": 0 }],
  "zones": [{ "x": 4, "y": -4, "z": 0 }]
}
```

Selector rules:

- Empty selector matches no units.
- Use `allUnits: true` when you intentionally want all units.
- Filled filter groups are combined with AND.
- Values inside one list are combined with OR.

## Useful reference files

- [Built-in maps](reference/BUILT_IN_MAPS.md)
- [Coordinates](reference/COORDINATES.md)
- [Enums](reference/ENUMS.md)
- [Units](reference/UNITS.md)
- [Traits](reference/TRAITS.md)
- [Payloads](reference/PAYLOADS.md)

## Common recipes

### Win when no enemy units remain

```json
"winConditionGroups": [
  {
    "conditions": [
      {
        "type": "NoUnitsMatch",
        "targets": { "allUnits": true, "aliveOnly": true, "teamIds": [1] }
      }
    ]
  }
]
```

### Trigger event when any allied unit enters a zone

```json
{
  "trigger": "UnitMoved",
  "conditions": [
    {
      "type": "AnyUnitMatches",
      "targets": { "aliveOnly": true, "teamIds": [0], "zones": [{ "x": 4, "y": -4, "z": 0 }] }
    }
  ],
  "actions": [{ "type": "SetFlag", "payload": "entered_target_zone" }],
  "executeOnce": true
}
```

### Survive until round 5

```json
"winConditionGroups": [
  { "conditions": [{ "type": "RoundAtLeast", "intValue": 5 }] }
]
```

### Temporary mission completion for testing campaign unlocks

Use this only while testing and remove it before publishing:

```json
"winConditionGroups": [
  { "conditions": [{ "type": "RoundAtLeast", "intValue": 1 }] }
],
"onWinActions": [{ "type": "EndMission", "payload": "win" }]
```

## Validation and publishing

The game validates manifests, entry paths, campaign mission paths, scenario graph structure, unknown trigger/condition/action types, unknown command ids, `SendCommand` payloads, unit selectors, popup thumbnail paths, and common campaign dependency errors.

1. Put your mod folder in `Documents/War Pawns/Mods/`.
2. Open the in-game Mods screen.
3. Check validation status.
4. If the mod has no `workshopId`, use Publish.
5. After successful publish, the game writes `workshopId` into `manifest.json`.
6. Future uploads should use Update.

## Known limitations

- JSON does not support comments.
- Video clips are not supported for custom JSON popups.
- Custom content cannot override base scenarios.
- One local mod equals one playable entry.
- Scenario IDs and campaign IDs must be globally unique.
- `workshopId` should be empty for new local mods.
- Use `payload`, not `key`, for JSON actions.
- Tutorial map is not recommended as a public template map.
