# 01 — Installing a template

This guide explains how to install a template mod into War Pawns.

## Local mod folder

War Pawns reads local mods from:

```text
Documents/War Pawns/Mods/
```

Each direct child folder inside `Mods` is treated as one local mod.

## Correct folder layout

Standalone scenario:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/
  manifest.json
  scenarios/template_scenario.scenario
  localization/en.json
  images/preview.png
  images/popup_thumbnail.png
  audio/README.md
```

Campaign:

```text
Documents/War Pawns/Mods/WarPawns_TemplateCampaign/
  manifest.json
  campaigns/template_campaign.campaign
  scenarios/mission_01.scenario
  scenarios/mission_02.scenario
  localization/en.json
  images/preview.png
  images/popup_thumbnail.png
  audio/README.md
```

## The manifest rule

The game expects `manifest.json` directly inside the mod folder.

Correct:

```text
Documents/War Pawns/Mods/MyMod/manifest.json
```

Wrong:

```text
Documents/War Pawns/Mods/MyMod/MyMod/manifest.json
```

## Validate in game

Open:

```text
Mods
```

Select your mod and check `Status`.

- `Valid` — playable and can be published/updated.
- `Warning` — playable, but something should be checked, such as game version mismatch or missing preview.
- `Invalid` — cannot be played until the listed errors are fixed.

## Play the template

Standalone scenario:

```text
Singleplayer -> Custom Scenarios -> Template Scenario -> Play
```

Campaign:

```text
Singleplayer -> Custom Campaigns -> Template Campaign -> Play
```

