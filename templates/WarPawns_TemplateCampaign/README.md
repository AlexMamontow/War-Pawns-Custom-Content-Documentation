# War Pawns Template Campaign

Copy this folder into `Documents/War Pawns/Mods/` and rename the folder, manifest id, campaign id, mission ids, and localization keys.

The second mission is locked until `template_campaign_mod.mission_01` is completed.

Useful files:

- `manifest.json` - mod metadata and campaign entry.
- `campaigns/template_campaign.campaign` - campaign mission list and unlock requirements.
- `scenarios/mission_01.scenario` - first playable mission.
- `scenarios/mission_02.scenario` - second playable mission.
- `localization/en.json` - campaign, mission, popup, and objective text.

For unlock tests, temporarily make mission 01 complete after round 1 by using a `RoundAtLeast` win condition. Remove that temporary condition before publishing.
