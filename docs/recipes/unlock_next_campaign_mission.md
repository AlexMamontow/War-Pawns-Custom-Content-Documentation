# Unlock the next campaign mission

Campaign unlocks are defined in the `.campaign` file.

Example:

```json
{
  "scenarioId": "my_campaign_mod.mission_02",
  "path": "scenarios/mission_02.scenario",
  "titleKey": "my_campaign.mission_02.title",
  "descriptionKey": "my_campaign.mission_02.description",
  "preview": "images/preview.png",
  "requiredScenarioIds": [
    "my_campaign_mod.mission_01"
  ]
}
```

This means mission 2 is locked until mission 1 is completed in the same campaign.

The player completes a mission when the scenario reaches `EndMission` through its win flow.

