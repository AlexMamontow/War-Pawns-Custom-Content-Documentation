# Temporary mission completion for testing

Use this to test campaign unlocks quickly.

Do not add a custom debug command. Temporarily replace the mission win condition with a simple round condition.

```json
"winConditionGroups": [
  {
    "conditions": [
      {
        "type": "RoundAtLeast",
        "intValue": 1
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

Start the mission, end the first turn, and check that the next campaign mission unlocks.

Remove this temporary condition before publishing.

