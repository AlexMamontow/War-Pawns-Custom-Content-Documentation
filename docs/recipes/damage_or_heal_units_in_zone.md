# Damage or heal units in a zone

Use `update_units` with a unit target selector.

Damage all living enemy units in a zone by 25% personnel:

```json
{
  "type": "SendCommand",
  "commandId": "update_units",
  "payload": "{"targets":{"aliveOnly":true,"teamIds":[1],"zones":[{"x":4,"y":-4,"z":0}]},"personnelDelta":-0.25}"
}
```

Heal all living allied units in a zone by 25% personnel:

```json
{
  "type": "SendCommand",
  "commandId": "update_units",
  "payload": "{"targets":{"aliveOnly":true,"teamIds":[0],"zones":[{"x":0,"y":0,"z":0}]},"personnelDelta":0.25}"
}
```

Kill units explicitly by setting personnel to zero:

```json
{
  "type": "SendCommand",
  "commandId": "update_units",
  "payload": "{"targets":{"unitIds":[10,11]},"personnel":0}"
}
```

