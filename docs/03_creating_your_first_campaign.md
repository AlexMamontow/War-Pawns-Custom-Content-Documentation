# 03 — Creating your first campaign

A campaign is a playable list of scenario files with optional unlock requirements.

Start from:

```text
templates/WarPawns_TemplateCampaign
```

## Step 1 — Copy the campaign template

Copy the folder into:

```text
Documents/War Pawns/Mods/
```

Rename it, for example:

```text
Documents/War Pawns/Mods/My_First_Campaign
```

## Step 2 — Rename the manifest

Open:

```text
manifest.json
```

Change:

```json
"id": "template_campaign_mod",
"campaignId": "template_campaign_mod.campaign"
```

to:

```json
"id": "my_first_campaign_mod",
"campaignId": "my_first_campaign_mod.campaign"
```

Keep:

```json
"contentType": "Campaign"
```

## Step 3 — Rename the campaign file IDs

Open:

```text
campaigns/template_campaign.campaign
```

Change:

```json
"campaignId": "my_first_campaign_mod.campaign"
```

Then rename mission IDs:

```json
"scenarioId": "my_first_campaign_mod.mission_01"
```

and:

```json
"scenarioId": "my_first_campaign_mod.mission_02"
```

If mission 2 requires mission 1, update the dependency too:

```json
"requiredScenarioIds": [
  "my_first_campaign_mod.mission_01"
]
```

## Step 4 — Rename IDs inside mission files

Open:

```text
scenarios/mission_01.scenario
scenarios/mission_02.scenario
```

Update their `scenarioId` fields to match the campaign file.

## Step 5 — Test mission unlocks

By default, mission 2 is locked until mission 1 is completed.

For quick testing, temporarily make mission 1 complete after round 1:

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

Start mission 1, end the first turn, and confirm mission 2 unlocks.

Remove this temporary win condition before publishing.

## Step 6 — Validate in game

Open:

```text
Mods
```

Expected status:

```text
Valid
```

Then open:

```text
Singleplayer -> Custom Campaigns
```

