# Payload reference

`SendCommand` actions use `commandId` and a string `payload`. The payload string usually contains JSON, so quotes inside it must be escaped inside the `.scenario` file.

Readable payload:

```json
{ "playerId": 0, "amount": 3, "clampToZero": true }
```

Inside `.scenario`:

```json
{
  "type": "SendCommand",
  "commandId": "give_resources",
  "payload": "{\"playerId\":0,\"amount\":3,\"clampToZero\":true}"
}
```

## `spawn_units`

Fields per unit:

| Field | Type | Description |
| --- | --- | --- |
| ownerPlayerId | int | Player that owns the spawned unit. |
| unitDataId | int | Per-nation unit index from UNITS.md. |
| position | Vector3Int | Requested cube coordinate. |
| experience | int | Initial experience. |
| personnel | float | Initial personnel, usually 0..1. |
| displayNameKey | string | Optional localization key for display name. |

If `position` is occupied, the game searches for the nearest available map hex. Units in the same batch reserve fallback positions so they do not stack.

## `update_units` patch fields

| Patch field | Type | Description |
| --- | --- | --- |
| ownerPlayerId | int | Change owner player. |
| teamId | int | Change team. |
| nationId | int | Change nation. |
| unitDataId | int | Change unit data id. |
| type | string/int | Change unit type. |
| position | Vector3Int | Move/reposition unit. |
| veteranLevel | int | Set veteran level. |
| personnel | float | Set personnel. |
| personnelDelta | float | Add/subtract personnel. |
| power | float/int | Set power. |
| movement | float/int | Set movement. |
| recon | float/int | Set recon. |
| powerDelta | float/int | Add/subtract power. |
| movementDelta | float/int | Add/subtract movement. |
| reconDelta | float/int | Add/subtract recon. |
| overrideTraits | bool | Replace full trait list when true. |
| traitIds | int[] | Replacement trait list. |
| addTraitIds | int[] | Traits to add. |
| removeTraitIds | int[] | Traits to remove. |
| displayNameKey | string | Set display name localization key. |

## `update_players` fields

| Field | Type | Description |
| --- | --- | --- |
| playerId | int | Target player. |
| hasResources | bool | Set true to apply resources. |
| resources | int | Resource value. |
| hasControlType | bool | Set true to apply controlType. |
| controlType | string | LocalHuman, AI, etc. |
| hasUnitsSpawnArea | bool | Set true to replace unitsSpawnArea. |
| unitsSpawnArea | Vector3Int[] | New spawn area list. |

## `give_resources`

Supports `playerId`, `playerIds`, `teamIds`, `allPlayers`, `amount`, and `clampToZero`. `amount` may be negative.

## `modify_unit_traits`

Supports `targets`, `addTraitIds`, `removeTraitIds`, `overrideTraits`, and `traitIds`.
