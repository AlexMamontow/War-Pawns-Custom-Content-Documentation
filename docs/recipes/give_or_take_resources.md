# Give or take resources

Use `give_resources`. The amount may be positive or negative.

Give player 0 three resources:

```json
{
  "type": "SendCommand",
  "commandId": "give_resources",
  "payload": "{"playerId":0,"amount":3,"clampToZero":true}"
}
```

Take two resources from player 0:

```json
{
  "type": "SendCommand",
  "commandId": "give_resources",
  "payload": "{"playerId":0,"amount":-2,"clampToZero":true}"
}
```

Use `clampToZero: true` if resources should not go below zero.

