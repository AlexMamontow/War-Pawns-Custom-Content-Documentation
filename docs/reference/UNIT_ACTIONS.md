# Unit action IDs

This page lists actions from the game's `ActionsConfig.Items` list.

Most custom scenario authors do **not** need these IDs for basic scenarios. Start with the scenario recipes first.

Use this page only when a payload, trait, or future documentation explicitly refers to a unit `actionId`.

Important distinction:

- **Unit actions** are actions a unit can perform in battle, such as movement, attack, sabotage, recruitment, or boost actions.
- **Scenario actions** are scenario scripting actions such as `ShowRegularPopup`, `SendCommand`, `HighlightZone`, or `EndMission`. Scenario actions are documented in [SCENARIO_REFERENCE.md](SCENARIO_REFERENCE.md).

The current public reference contains action IDs `0` through `34`.

| actionId | Name | Type |
| ---: | --- | --- |
| 0 | `MovementAction` | Movement Action |
| 1 | `AttackAction` | Attack Action |
| 2 | `FillNonInfantryPersonnelAction` | Fill Personnel Action |
| 3 | `FillInfantryPersonnelAction` | Fill Personnel Action |
| 4 | `SniperShot` | Distant Attack Action |
| 5 | `ArtilleryStrike` | Distant Attack Action |
| 6 | `Raid` | Raid Action |
| 7 | `NonCapturingMovementAction` | Movement Action |
| 8 | `ThrowATGrenade` | Throw Grenade With Response Action |
| 9 | `FortifyPositionAction` | Change Detail And Trait Action |
| 10 | `ThrowGrenade` | Throw Grenade With Response Action |
| 11 | `ReconRaid` | Raid Action |
| 12 | `PlaceWiredFenceAction` | Change Detail And Trait Action |
| 13 | `PlaceHedgehogAction` | Change Detail And Trait Action |
| 14 | `PlaceLandmineAction` | Change Detail And Trait Action |
| 15 | `DemolishAction` | Change Detail And Trait Action |
| 16 | `DeminingAction` | Change Detail And Trait Action |
| 17 | `SwapUnitsAction` | Swap Units Action |
| 18 | `AirStrikeAction` | Air Strike Action |
| 19 | `AdjacentMoveAction` | Adjacent Move Action |
| 20 | `BoostDefenceAction` | Granting Trait Action |
| 21 | `BoostAttackAction` | Granting Trait Action |
| 22 | `ReconAreaAction` | Recon Area Action |
| 23 | `SabotageAction` | Granting Trait Action |
| 24 | `EncourageAction` | Granting Trait Action |
| 25 | `ISUStrike` | Distant Attack Action |
| 26 | `SabotageInfAction` | Granting Trait Action |
| 27 | `GuardAllyInfAction` | Granting Trait Action |
| 28 | `GuardAllyTankAction` | Granting Trait Action |
| 29 | `OfficerEncourageAction` | Granting Trait Action |
| 30 | `RecruitmentAction` | Spawn Unit Action |
| 31 | `FillSelfPersonnelAction` | Fill Personnel Action |
| 32 | `PlaceFieldCamp` | Change Detail And Trait Action |
| 33 | `MovementDisruptionAction` | Granting Trait Action |
| 34 | `MovementBoostAction` | Granting Trait Action |
