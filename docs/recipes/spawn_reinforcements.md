# Spawn reinforcements

Use `spawn_units` to add units during a scenario.

Example action:

```json
{
  "type": "SendCommand",
  "commandId": "spawn_units",
  "payload": "{"units":[{"ownerPlayerId":0,"unitDataId":2,"position":{"x":4,"y":-12,"z":8},"personnel":1.0,"experience":0}]}"
}
```

Important:

- `ownerPlayerId` must exist in the scenario `players` list.
- `unitDataId` depends on that player's `nationId`.
- `position` must be valid for the selected map.
- If the position is occupied, the game tries to find a nearby free hex.

References:

- [../06_using_ids.md](../06_using_ids.md)
- [../reference/UNITS.md](../reference/UNITS.md)
- [../reference/COORDINATES.md](../reference/COORDINATES.md)
