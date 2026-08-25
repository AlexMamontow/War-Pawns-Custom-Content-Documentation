# Spawn reinforcements

Use `SendCommand` with `commandId: "spawn_units"`.

```json
{
  "type": "SendCommand",
  "commandId": "spawn_units",
  "payload": "{"units":[{"ownerPlayerId":0,"unitDataId":2,"position":{"x":1,"y":-1,"z":0},"experience":0,"personnel":1.0,"displayNameKey":"my_mod.unit.reinforcement"}]}"
}
```

Notes:

- `ownerPlayerId` must exist in `players`.
- `unitDataId` is the unit index for the owner's nation. See `docs/reference/UNITS.md`.
- `position` uses cube coordinates. See `docs/reference/COORDINATES.md`.
- If the requested hex is occupied, the game tries to use the nearest available hex.

