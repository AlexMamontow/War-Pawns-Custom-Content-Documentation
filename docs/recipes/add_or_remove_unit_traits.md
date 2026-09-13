# Add or remove unit traits

Use `modify_unit_traits` when you want to add, remove, or override traits on selected units.

This example adds `EncourageGrantingTrait` to all living allied infantry.

`EncourageGrantingTrait` is `traitId` 68.

```json
{
  "type": "SendCommand",
  "commandId": "modify_unit_traits",
  "payload": "{"targets":{"aliveOnly":true,"teamIds":[0],"unitTypes":["Infantry"]},"addTraitIds":[68]}"
}
```

Remove a trait:

```json
{
  "type": "SendCommand",
  "commandId": "modify_unit_traits",
  "payload": "{"targets":{"aliveOnly":true,"teamIds":[1]},"removeTraitIds":[72]}"
}
```

Useful new traits:

```text
68 = EncourageGrantingTrait
69 = RecruitmentGrantingTrait
70 = FieldCampGrantingTrait
71 = MovementDisruptionGrantingTrait
72 = MovementDisruptionDebuffTrait
73 = MovementBoostGrantingTrait
74 = MovementBoostTrait
75 = MovementBoostTrait
```

Full list: [../reference/TRAITS.md](../reference/TRAITS.md)
