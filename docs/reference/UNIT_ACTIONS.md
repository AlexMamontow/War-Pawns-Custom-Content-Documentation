# Unit action IDs

Unit `actionId` is the **index** in `ActionsConfig.Items`. This reference is mostly for advanced modders and for checking the game's action catalog.

**Do not confuse:**
- **Unit actions**: battle commands a unit can perform (`MovementAction`, `AttackAction`, `ATGunStrike`).
- **Scenario actions**: entries in a `.scenario` graph (`SendCommand`, `EndMission`, `ShowRegularPopup`). See [SCENARIO_REFERENCE.md](SCENARIO_REFERENCE.md).

Adding a unit to a scenario uses `unitDataId`, **not** `actionId`. See [UNITS.md](UNITS.md).

## Full `ActionsConfig.Items` list

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
| 35 | `ATGunStrike` | Distant Attack Action |

## New unit action (2026-10-17)

`35` — `ATGunStrike` (`Distant Attack Action`).

This is a **unit action**, not an additional `ActionType` or scenario `commandId`. The screenshot shows its name/index/category, but it does not establish its range, damage, or eligibility rules.

[Download machine-readable action list (CSV)](unit_actions.csv)
