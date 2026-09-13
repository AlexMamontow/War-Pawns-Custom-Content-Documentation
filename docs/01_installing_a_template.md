# Installing a template

This page explains only installation. It does not explain scenario editing.

## Local mods folder

War Pawns reads local mods from:

```text
Documents/War Pawns/Mods/
```

Each mod must be one folder inside `Mods`.

## Install the standalone scenario template

Copy:

```text
templates/WarPawns_TemplateScenario
```

to:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario
```

Correct final structure:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
Documents/War Pawns/Mods/WarPawns_TemplateScenario/scenarios/template_scenario.scenario
Documents/War Pawns/Mods/WarPawns_TemplateScenario/localization/en.json
Documents/War Pawns/Mods/WarPawns_TemplateScenario/images/preview.png
```

## Install the campaign template

Copy:

```text
templates/WarPawns_TemplateCampaign
```

to:

```text
Documents/War Pawns/Mods/WarPawns_TemplateCampaign
```

Correct final structure:

```text
Documents/War Pawns/Mods/WarPawns_TemplateCampaign/manifest.json
Documents/War Pawns/Mods/WarPawns_TemplateCampaign/campaigns/template_campaign.campaign
Documents/War Pawns/Mods/WarPawns_TemplateCampaign/scenarios/mission_01.scenario
Documents/War Pawns/Mods/WarPawns_TemplateCampaign/scenarios/mission_02.scenario
```

## How to confirm it worked

Open War Pawns and go to:

```text
Mods
```

A correctly installed template should appear there and show `Valid`.

Then open:

```text
Singleplayer -> Custom Scenarios
```

or:

```text
Singleplayer -> Custom Campaigns
```

## Common install mistake

Do not create this structure:

```text
Documents/War Pawns/Mods/MyMod/MyMod/manifest.json
```

The correct structure is:

```text
Documents/War Pawns/Mods/MyMod/manifest.json
```
