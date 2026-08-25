# Trigger a popup when a unit enters a zone

Use `UnitMoved` plus `AnyUnitMatches`.

Add this branch to a scenario step:

```json
{
  "id": "player_entered_target_zone",
  "name": "Player entered target zone",
  "trigger": "UnitMoved",
  "executeOnce": true,
  "conditions": [
    {
      "type": "AnyUnitMatches",
      "targets": {
        "aliveOnly": true,
        "teamIds": [0],
        "zones": [
          { "x": 4, "y": -4, "z": 0 }
        ]
      }
    }
  ],
  "actions": [
    {
      "type": "ShowRegularPopup",
      "popup": {
        "pages": [
          {
            "title": "my_mod.popup.zone.title",
            "body": "my_mod.popup.zone.body",
            "thumbnail": "images/popup_thumbnail.png"
          }
        ]
      }
    },
    {
      "type": "SetFlag",
      "payload": "player_entered_target_zone"
    }
  ]
}
```

Add the text keys to `localization/en.json`.

