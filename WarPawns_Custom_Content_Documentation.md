# War Pawns Custom Content Guide

This guide describes the v1 local/Workshop custom content format for War Pawns.

## Folder location

Local mods are placed here:

```text
Documents/War Pawns/Mods/
```

A mod folder should contain a `manifest.json` at its root. One local mod is one playable entry: either a standalone scenario or a campaign.

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
  "localization": [
    { "language": "en", "path": "localization/en.json" }
  ],
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
  "localization": [
    { "language": "en", "path": "localization/en.json" }
  ],
  "workshopId": ""
}
```

`gameVersion` may be empty. If it is set and differs from the current game version, the mod remains playable but the UI will show a warning.

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

## Scenario file overview

A `.scenario` file contains setup data and a scenario graph:

```json
{
  "formatVersion": 1,
  "scenarioId": "my_mod.scenario_01",
  "titleKey": "my_mod.scenario.title",
  "map": { "id": "afccd13f3a754d49aa010c63dc297084" },
  "rules": {},
  "players": [],
  "initialUnits": [],
  "initialZones": [],
  "graph": {}
}
```

The map can be a base-game map id or a mod-relative map file path. Use only one:

```json
"map": { "id": "base_map_id" }
```

or:

```json
"map": { "path": "maps/my_map.map" }
```

## Scenario graph

The graph contains steps and the main objective.

```json
"graph": {
  "entryStepId": "main",
  "steps": [
    {
      "stepId": "main",
      "playerObjectivesText": ["my_mod.objective.main"],
      "onEnterActions": [],
      "onExitActions": [],
      "branches": []
    }
  ],
  "mainObjective": {
    "playerObjectivesText": ["my_mod.objective.main"],
    "onStartActions": [],
    "triggerActions": [],
    "winConditionGroups": [],
    "onWinActions": [],
    "loseConditionGroups": [],
    "onLoseActions": []
  }
}
```

A branch can transition to another step or run actions without changing step. Empty `nextStepId` means action-only branch.

Condition groups in win/lose objectives use OR between groups and AND inside each group.

## Available triggers

- `ScenarioStarted` — fires when the scenario starts.
- `AnyEvent` — fires on any executed game command, not on scenario start.
- `TurnEnded` — fires after an end-turn command.
- `TurnStarted` — fires after an end-turn command; use current player/team conditions to target a specific turn.
- `RoundStarted` — fires when a new round starts.
- `ZoneCaptured` — fires after movement, attack, or scripted ownership change commands that may change zone ownership.
- `UnitAttacked` — fires after attack or scenario artillery strike.
- `UnitMoved` — fires after movement, adjacent move, or swap command.
- `UnitKilled` — fires when one or more units changed from alive to dead after a command.

## Available conditions

- `AlwaysTrue`
- `FlagTrue` — `key` flag exists.
- `FlagFalse` — `key` flag does not exist.
- `IntAtLeast` — counter `key` is at least `intValue`.
- `TeamControlsZones` — `teamId` controls all `zones`. `teamId: -1` means any non-neutral team.
- `UnitsDead` — all `unitIds` are dead.
- `AnyUnitMatches` — at least one unit matches `targets`.
- `NoUnitsMatch` — zero units match `targets`.
- `UnitCountAtLeast` — matching unit count is at least `intValue`.
- `UnitCountAtMost` — matching unit count is at most `intValue`.
- `RoundAtLeast` — current round number is at least `intValue`.
- `RoundEquals` — current round number equals `intValue`.
- `CurrentPlayerIs` — current player is `playerId` or one of `playerIds`.
- `CurrentTeamIs` — current team is `teamId` or one of `teamIds`.
- `PlayerResourcesAtLeast` — all selected players have at least `intValue` resources.
- `PlayerResourcesAtMost` — all selected players have at most `intValue` resources.
- `TeamResourcesAtLeast` — all selected teams have at least `intValue` total resources.
- `TeamResourcesAtMost` — all selected teams have at most `intValue` total resources.

## Unit target selector

Unit selector filters are used by unit conditions and several commands.

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
  "unitTypeIds": [],
  "hexes": [{ "x": 0, "y": 0, "z": 0 }],
  "zones": [{ "x": 4, "y": -4, "z": 0 }]
}
```

Rules:

- Empty selector matches no units.
- Use `allUnits: true` when you intentionally want to start from all units.
- Filled filter groups are combined with AND.
- Values inside one list are combined with OR.
- `hexes` and `zones` both check occupied unit positions.

## Available actions

- `ShowUnitMessagePopup`
- `ShowRegularPopup`
- `ShowTutorialPopup`
- `ShowNarrationPopup`
- `HighlightZone`
- `ClearHighlightZone`
- `SetFlag`
- `AddCounter`
- `SendCommand`
- `EndMission`

Popup page fields:

```json
{
  "title": "my_mod.popup.title",
  "body": "my_mod.popup.body",
  "audioKey": "my_mod.radio_01",
  "thumbnail": "images/popup_thumbnail.png"
}
```

`thumbnail` and `thumbnailPath` are mod-relative. Video clips are not supported for JSON custom popups in v1.

`SetFlag`, `AddCounter`, `EndMission`, and `SendCommand` use the `payload` field. For `EndMission`, include `"win"` in payload to save campaign progress and completion achievements.

## SendCommand and payload strings

`SendCommand` actions use `commandId` and `payload`. The `payload` value is a string that contains JSON, so quotes inside it must be escaped in the `.scenario` file.

Readable payload:

```json
{ "playerId": 0, "amount": 3, "clampToZero": true }
```

Inside `.scenario`:

```json
{
  "type": "SendCommand",
  "commandId": "give_resources",
  "payload": "{\\"playerId\\":0,\\"amount\\":3,\\"clampToZero\\":true}"
}
```

## Available commands

### `promote_player_officer`

```json
{ "unitId": 0, "targetRank": 4, "save": true }
```

### `update_recruitable_units`

```json
{
  "nations": [
    { "nationId": 3, "allowAll": false, "unitDataIds": [0, 1, 2] }
  ]
}
```

### `spawn_units`

```json
{
  "units": [
    {
      "ownerPlayerId": 0,
      "unitDataId": 1,
      "position": { "x": 1, "y": -1, "z": 0 },
      "experience": 0,
      "personnel": 1.0,
      "displayNameKey": "my_mod.unit.reinforcement"
    }
  ]
}
```

If the requested spawn hex is occupied, the game searches for the nearest available map hex. Units in the same spawn batch reserve their fallback positions so they do not stack on one fallback hex.

### `update_units`

Explicit unit mode:

```json
{
  "units": [
    { "targetUnitId": 10, "personnel": 0.5, "addTraitIds": [12] }
  ]
}
```

Selector patch mode:

```json
{
  "targets": { "aliveOnly": true, "teamIds": [1], "zones": [{ "x": 4, "y": -4, "z": 0 }] },
  "patch": { "personnelDelta": -0.25, "clampPersonnel": true }
}
```

Useful patch fields: `ownerPlayerId`, `teamId`, `nationId`, `unitDataId`, `type`, `position`, `veteranLevel`, `personnel`, `personnelDelta`, `power`, `movement`, `recon`, `powerDelta`, `movementDelta`, `reconDelta`, `overrideTraits`, `traitIds`, `addTraitIds`, `removeTraitIds`, `overrideActions`, `actionIds`, `displayOrdinal`, `displayNameKey`.

### `update_players`

```json
{
  "players": [
    { "playerId": 0, "hasResources": true, "resources": 10 }
  ]
}
```

Supported player fields: `hasResources`, `resources`, `hasControlType`, `controlType`, `hasUnitsSpawnArea`, `unitsSpawnArea`.

### `give_resources`

```json
{ "playerId": 0, "amount": -3, "clampToZero": true }
```

`amount` may be positive or negative. You can also use `playerIds`, `teamIds`, or `allPlayers`.

### `modify_unit_traits`

```json
{
  "targets": { "aliveOnly": true, "teamIds": [0], "unitTypes": ["Infantry"] },
  "addTraitIds": [12],
  "removeTraitIds": [3]
}
```

Use `overrideTraits: true` with `traitIds` to replace the full trait list.

### `unlock_steam_achievement`

For this command, `payload` is the achievement API name directly:

```json
{
  "type": "SendCommand",
  "commandId": "unlock_steam_achievement",
  "payload": "ACH_FIRST_BLOOD"
}
```

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
  "actions": [
    { "type": "SetFlag", "payload": "entered_target_zone" }
  ],
  "executeOnce": true
}
```

### Survive until round 5

```json
"winConditionGroups": [
  { "conditions": [{ "type": "RoundAtLeast", "intValue": 5 }] }
]
```

### Damage all enemy units in a zone

Readable command payload:

```json
{
  "targets": { "aliveOnly": true, "teamIds": [1], "zones": [{ "x": 4, "y": -4, "z": 0 }] },
  "patch": { "personnelDelta": -0.25, "clampPersonnel": true }
}
```

### Add a trait to all allied infantry

Readable command payload:

```json
{
  "targets": { "aliveOnly": true, "teamIds": [0], "unitTypes": ["Infantry"] },
  "addTraitIds": [12]
}
```

## Validation notes

The game validates mod manifests, entry paths, campaign mission paths, scenario graph structure, unknown trigger/condition/action types, unknown command ids, SendCommand payloads, unit selector conditions, popup thumbnail paths, and common campaign dependency errors.

Warnings generally do not block playing; errors do.

## Publishing workflow

1. Put your mod folder in `Documents/War Pawns/Mods/`.
2. Open the in-game Mods screen.
3. Check validation status.
4. If the mod has no `workshopId`, use Publish.
5. After successful publish, the game writes `workshopId` into `manifest.json`.
6. Future uploads should use Update.
