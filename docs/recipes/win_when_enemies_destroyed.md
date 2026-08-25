# Win when all enemies are destroyed

Use this when the player should win after no enemy units remain on the map.

Put this inside `graph.mainObjective`:

```json
"winConditionGroups": [
  {
    "conditions": [
      {
        "type": "NoUnitsMatch",
        "targets": {
          "allUnits": true,
          "aliveOnly": true,
          "teamIds": [1]
        }
      }
    ]
  }
],
"onWinActions": [
  {
    "type": "EndMission"
  }
]
```

`teamIds: [1]` usually means the enemy team when the local player is on team `0`.

