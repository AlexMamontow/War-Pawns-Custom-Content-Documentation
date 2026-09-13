# Using IDs in War Pawns custom content

Custom scenarios use IDs to refer to maps, players, teams, nations, units, traits, and actions.

This page explains which ID to use where.

## Mod, scenario, and campaign IDs

Use globally unique text IDs.

Good:

```text
my_first_scenario
my_first_scenario.main
my_campaign.mission_01
```

Avoid:

```text
mission_01
scenario
new_mod
```

Short generic IDs can conflict with other mods.

## playerId

`playerId` is defined inside each scenario's `players` list.

Use `playerId` when assigning starting units:

```json
"ownerPlayerId": 0
```

That means the unit belongs to the player whose `playerId` is `0`.

## teamId

Use `teamId` for allies/enemies and win conditions.

Common setup:

```text
teamId 0 = player/allies
teamId 1 = enemies
teamId 2 = observers
```

For scenario logic, prefer `teamIds` when possible. They are easier to understand than individual `playerId` values.

Example: win when no living enemy units remain:

```json
{
  "type": "NoUnitsMatch",
  "targets": {
    "allUnits": true,
    "aliveOnly": true,
    "teamIds": [1]
  }
}
```

## nationId

Use `nationId` inside `players`.

Common values:

```text
0 = Germany
1 = USSR
2 = Britain
3 = USA
4 = Japan
```

## unitDataId

`unitDataId` is the unit index inside that nation's unit list.

Example:

```json
{
  "ownerPlayerId": 0,
  "unitDataId": 2
}
```

If player `0` has `nationId` USA, `unitDataId: 2` means USA Riflemen.

If player `0` has `nationId` Germany, `unitDataId: 2` means Germany Riflemen.

Unit lists: [reference/UNITS.md](reference/UNITS.md)

## traitId

Use `traitId` when adding, removing, or overriding unit traits.

Trait list: [reference/TRAITS.md](reference/TRAITS.md)

Example:

```json
"addTraitIds": [68]
```

## actionId

Unit action IDs are rarely needed for beginner scenario scripting.

Unit action list: [reference/UNIT_ACTIONS.md](reference/UNIT_ACTIONS.md)

Do not confuse unit actions with scenario actions.

- Unit action: `MovementAction`, `AttackAction`, `RecruitmentAction`
- Scenario action: `SendCommand`, `ShowRegularPopup`, `EndMission`

Scenario actions are documented here:

[reference/SCENARIO_REFERENCE.md](reference/SCENARIO_REFERENCE.md)
