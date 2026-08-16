# Scenario reference

## Triggers

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

## Conditions

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

## Actions

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

## Commands

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

| Field | Type | Description |
| --- | --- | --- |
| allUnits | bool | When true, starts from all units. Empty selectors match nothing. |
| aliveOnly | bool | When true, ignore dead units. |
| unitIds | int[] | Specific runtime unit ids. |
| ownerPlayerIds | int[] | Units owned by these players. |
| teamIds | int[] | Units belonging to these teams. |
| nationIds | int[] | Units of these nations. |
| unitDataIds | int[] | Per-nation unit data indexes from UNITS.md. |
| unitTypes | string[] | Enum names such as Infantry, Tank, Artillery. |
| unitTypeIds | int[] | UnitType enum indexes. |
| hexes | Vector3Int[] | Specific occupied unit coordinates. |
| zones | Vector3Int[] | Zone coordinates; units standing on these hexes match. |

Selector rules:

- Empty selector matches no units.
- Use `allUnits: true` when you intentionally want to match all units.
- Filled filter groups are combined with AND.
- Values inside one list are combined with OR.
- `hexes` and `zones` both compare to occupied unit positions.
