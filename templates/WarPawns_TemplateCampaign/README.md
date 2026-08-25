# WarPawns_TemplateCampaign

This is a working two-mission custom campaign template.

Mission 2 is locked until mission 1 is completed.

## Install

Copy this entire folder to:

```text
Documents/War Pawns/Mods/WarPawns_TemplateCampaign
```

The final path must be:

```text
Documents/War Pawns/Mods/WarPawns_TemplateCampaign/manifest.json
```

Then launch War Pawns and open:

```text
Mods
```

Expected status:

```text
Valid
```

Play it from:

```text
Singleplayer -> Custom Campaigns -> Template Campaign -> Play
```

## Files

| File | Purpose |
| --- | --- |
| `manifest.json` | Tells the game this folder is a custom campaign mod |
| `campaigns/template_campaign.campaign` | Campaign mission list and unlock requirements |
| `scenarios/mission_01.scenario` | First campaign mission |
| `scenarios/mission_02.scenario` | Second campaign mission |
| `localization/en.json` | Campaign, mission, objective, popup, and unit text |
| `images/preview.png` | Campaign/mission preview image |
| `images/popup_thumbnail.png` | Example popup image |
| `audio/` | Optional audio files |

## How mission unlock works

Mission 2 has this dependency in `campaigns/template_campaign.campaign`:

```json
"requiredScenarioIds": [
  "template_campaign_mod.mission_01"
]
```

This means mission 2 unlocks only after mission 1 is completed.

## Testing unlocks quickly

To test campaign unlocks, temporarily make mission 1 complete after round 1. See:

```text
docs/recipes/temporary_mission_completion_for_testing.md
```

Remove the temporary test win condition before publishing.

