# Add or remove unit traits

Use `modify_unit_traits`.

Add trait `68` to all living allied infantry:

```json
{
  "type": "SendCommand",
  "commandId": "modify_unit_traits",
  "payload": "{"targets":{"aliveOnly":true,"teamIds":[0],"unitTypes":["Infantry"]},"addTraitIds":[68]}"
}
```

Remove trait `4` from specific units:

```json
{
  "type": "SendCommand",
  "commandId": "modify_unit_traits",
  "payload": "{"targets":{"unitIds":[10,11]},"removeTraitIds":[4]}"
}
```

Trait IDs are listed in `docs/reference/TRAITS.md`.

