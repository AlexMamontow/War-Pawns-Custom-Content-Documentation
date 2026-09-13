# Creating your first campaign

Start from `templates/WarPawns_TemplateCampaign`.

A campaign mod has one `manifest.json`, one `.campaign` file, and one or more `.scenario` files.

## 1. Copy the campaign template

Copy:

```text
templates/WarPawns_TemplateCampaign
```

to:

```text
Documents/War Pawns/Mods/MyFirstCampaign
```

## 2. Understand the files

```text
MyFirstCampaign/
  manifest.json
  campaigns/template_campaign.campaign
  scenarios/mission_01.scenario
  scenarios/mission_02.scenario
  localization/en.json
```

`manifest.json` tells the game this is a campaign mod.

`template_campaign.campaign` lists the campaign missions and unlock rules.

Each `.scenario` file is a playable mission.

## 3. Campaign manifest

For a campaign, `manifest.json` must use:

```json
"contentType": "Campaign",
"entry": "campaigns/template_campaign.campaign"
```

The `campaignId` in the manifest should match the `campaignId` in the `.campaign` file.

## 4. Campaign file

A minimal campaign has a list of scenarios:

```json
"scenarios": [
  {
    "scenarioId": "my_campaign.mission_01",
    "path": "scenarios/mission_01.scenario"
  },
  {
    "scenarioId": "my_campaign.mission_02",
    "path": "scenarios/mission_02.scenario",
    "requiredScenarioIds": ["my_campaign.mission_01"]
  }
]
```

This means:

- mission 1 is available immediately
- mission 2 unlocks after mission 1 is completed

## 5. Mission scenario IDs must match

If the campaign file says:

```json
"scenarioId": "my_campaign.mission_01"
```

then `scenarios/mission_01.scenario` must also contain:

```json
"scenarioId": "my_campaign.mission_01"
```

If these do not match, the campaign can become invalid or the mission will not launch.

## 6. Testing campaign unlocks

For testing, you can temporarily make mission 1 complete immediately or after round 1.

Use this recipe:

[recipes/temporary_mission_completion_for_testing.md](recipes/temporary_mission_completion_for_testing.md)

Remove the temporary win condition before publishing.
