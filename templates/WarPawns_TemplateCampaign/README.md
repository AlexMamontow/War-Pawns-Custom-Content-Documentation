# WarPawns_TemplateCampaign

This is a working two-mission campaign template.

Use it after you have already tested the standalone scenario template.

## Install

Copy this entire folder to:

```text
Documents/War Pawns/Mods/WarPawns_TemplateCampaign
```

The final path must be:

```text
Documents/War Pawns/Mods/WarPawns_TemplateCampaign/manifest.json
```

Launch War Pawns, open `Mods`, and check that the template is `Valid`.

Then open:

```text
Singleplayer -> Custom Campaigns
```

## Files

```text
manifest.json                         tells the game this is a campaign mod
campaigns/template_campaign.campaign  mission list and unlock rules
scenarios/mission_01.scenario          first mission
scenarios/mission_02.scenario          second mission
localization/en.json                   visible text and audio keys
images/preview.png                     campaign and mission preview image
images/popup_thumbnail.png             popup image used by the template
```

## How mission unlock works

Mission 2 contains:

```json
"requiredScenarioIds": ["template_campaign_mod.mission_01"]
```

This means mission 2 unlocks only after mission 1 is completed.

For testing unlocks, use:

[../../docs/recipes/temporary_mission_completion_for_testing.md](../../docs/recipes/temporary_mission_completion_for_testing.md)

Useful guides:

- [../../START_HERE.md](../../START_HERE.md)
- [../../docs/03_creating_your_first_campaign.md](../../docs/03_creating_your_first_campaign.md)
- [../../docs/05_using_maps.md](../../docs/05_using_maps.md)
- [../../docs/TROUBLESHOOTING.md](../../docs/TROUBLESHOOTING.md)
