# Trait IDs (game config reference)

`traitId` is the **numeric index** in `TraitsConfig.Items`, not a text name. Use it in `traitIds`, `addTraitIds`, `removeTraitIds`, and officer-trait configuration when the relevant scenario field expects an ID.

If this is your first scenario, start with [Using IDs](../06_using_ids.md) and [Add or remove traits](../recipes/add_or_remove_unit_traits.md) before using the table below.

Example: grant the `QuickLearners` trait (`traitId: 80`) to living units on team 0. In the `.scenario` file, `payload` is a JSON-encoded **string**, not a nested object:

```json
{
  "type": "SendCommand",
  "commandId": "modify_unit_traits",
  "payload": "{\"targets\":{\"allUnits\":true,\"aliveOnly\":true,\"teamIds\":[0]},\"addTraitIds\":[80]}"
}
```

**Important distinctions:**
- Trait IDs and unit action IDs are different. Some traits *grant* a unit action, but the trait is still selected by `traitId`.
- The unit action reference is [UNIT_ACTIONS.md](UNIT_ACTIONS.md); scenario scripting actions such as `SendCommand` belong to [SCENARIO_REFERENCE.md](SCENARIO_REFERENCE.md).
- Current screenshots confirm the new traits `78–82` and the order of `55–77`.
- **ID 54 needs confirmation.** It was not visible in the supplied updated screenshots. The old documentation listed `SabotageDebuffTrait` at 54, but the newer screenshots unambiguously show it at **55**. Rather than publish an incorrect ID, this one entry is marked **UNVERIFIED** until a screenshot of `TraitsConfig.Items` around index 54 is supplied. All other rows are retained from earlier reference material or confirmed screenshots.

## Full ID list

| traitId | Name | Type |
| ---: | --- | --- |
| 0 | `NoneTrait` | None Trait |
| 1 | `LightCover` | Passive Combat Bonus Trait |
| 2 | `FortifiedPosition` | Passive Combat Bonus Trait |
| 3 | `WireFence` | Passive Regular Bonus Trait |
| 4 | `Hedgehogs` | Passive Regular Bonus Trait |
| 5 | `Landmines` | Passive Regular Bonus Trait |
| 6 | `ArtillerySchool` | Global Regular Bonus Trait |
| 7 | `AssaultRifles` | Passive Combat Bonus Trait |
| 8 | `Bazooka` | Passive Combat Bonus Trait |
| 9 | `BoltActionRifles` | Passive Combat Bonus Trait |
| 10 | `CommandFavor` | Resource Bonus Trait |
| 11 | `DreadedReputation` | Positional Combat Radius Trait |
| 12 | `DrillInstructor` | Global Regular Bonus Trait |
| 13 | `EffectiveAgainstInfantry` | Passive Combat Bonus Trait |
| 14 | `EffectiveAgainstTanks` | Passive Combat Bonus Trait |
| 15 | `EffectiveAgainstVehicles` | Passive Combat Bonus Trait |
| 16 | `EffectiveAttacker` | Passive Combat Bonus Trait |
| 17 | `EffectiveDefender` | Passive Combat Bonus Trait |
| 18 | `EliteAssaultRifles` | Passive Combat Bonus Trait |
| 19 | `EliteMachinegun` | Passive Combat Bonus Trait |
| 20 | `Engineer` | Ignore Self Traits Trait |
| 21 | `HeavyHowitzer` | Passive Combat Bonus Trait |
| 22 | `Howitzer` | Passive Combat Bonus Trait |
| 23 | `PersonalGuard` | Passive Regular Bonus Trait |
| 24 | `LightMachinegun` | Passive Combat Bonus Trait |
| 25 | `LogisticsMastery` | Improved Healing Trait |
| 26 | `Machinegun` | Passive Combat Bonus Trait |
| 27 | `MotivationSpeech` | Positional Combat Radius Trait |
| 28 | `Panzershreck` | Passive Combat Bonus Trait |
| 29 | `Raider` | Combat Bonus Trait |
| 30 | `ReconTraining` | Global Regular Bonus Trait |
| 31 | `SemiAutoRifles` | Passive Combat Bonus Trait |
| 32 | `ImprovedOptics` | Global Regular Bonus Trait |
| 33 | `ShootingInstructor` | Global Regular Bonus Trait |
| 34 | `SniperRifle` | Passive Combat Bonus Trait |
| 35 | `SpecialForces` | Global Regular Bonus Trait |
| 36 | `SpecialTraining` | Passive Combat Bonus Trait |
| 37 | `TankDestroyer` | Passive Combat Bonus Trait |
| 38 | `SkilledCommander` | Passive Regular Bonus Trait |
| 39 | `Flamethrower` | Ignore Opponent Combat Traits |
| 40 | `OffensiveDoctrine` | Global Combat Bonus Trait |
| 41 | `DefensiveDoctrine` | Global Combat Bonus Trait |
| 42 | `Aggressive` | Positional Combat Radius Trait |
| 43 | `Napalm` | Passive Combat Bonus Trait |
| 44 | `SwapTrait` | Granting Action Trait |
| 45 | `EliteInfantry` | Passive Combat Bonus Trait |
| 46 | `AirStrikeTrait` | Granting Action Trait |
| 47 | `AdjacentMoveTrait` | Granting Action Trait |
| 48 | `BoostedDefence` | Passive Combat Bonus Trait |
| 49 | `BoostedAttack` | Passive Combat Bonus Trait |
| 50 | `LightHowitzer` | Passive Combat Bonus Trait |
| 51 | `DefenseExpertise` | Positional Regular Radius Trait |
| 52 | `ReconAreaTrait` | Granting Action Trait |
| 53 | `SabotageGrantingTrait` | Granting Action Trait |
| 54 | **Not verified — see note above** | Needs verification |
| 55 | `SabotageDebuffTrait` | Passive Regular Bonus Trait |
| 56 | `SuppressionFire` | Positional Combat Radius Trait |
| 57 | `Encouraged` | Passive Combat Bonus Trait |
| 58 | `Deadly` | Passive Combat Bonus Trait |
| 59 | `Sturdy` | Passive Combat Bonus Trait |
| 60 | `TankVeteran` | Passive Combat Bonus Trait |
| 61 | `HeavyTankDestroyer` | Passive Combat Bonus Trait |
| 62 | `Guarded` | Passive Combat Bonus Trait |
| 63 | `SabotageInfDebuffTrait` | Passive Regular Bonus Trait |
| 64 | `IntensiveSpecialTraining` | Passive Combat Bonus Trait |
| 65 | `ImprovedSniperRifle` | Passive Combat Bonus Trait |
| 66 | `EncouragedByOfficer` | Passive Regular Bonus Trait |
| 67 | `CommanderPresence` | Positional Regular Radius Trait |
| 68 | `ReconDisruption` | Positional Regular Radius Trait |
| 69 | `EncourageGrantingTrait` | Granting Action Trait |
| 70 | `RecruitmentGrantingTrait` | Granting Action Trait |
| 71 | `FieldCampGrantingTrait` | Granting Action Trait |
| 72 | `MovementDisruptionGrantingTrait` | Granting Action Trait |
| 73 | `MovementDisruptionDebuffTrait` | Passive Regular Bonus Trait |
| 74 | `MovementBoostGrantingTrait` | Granting Action Trait |
| 75 | `MovementBoostTrait` | Passive Regular Bonus Trait |
| 76 | `Supplies` | Positional Regular Radius Trait |
| 77 | `LightArmor` | Passive Combat Bonus Trait |
| 78 | `HeavyATGun` | Passive Combat Bonus Trait |
| 79 | `ATGun` | Passive Combat Bonus Trait |
| 80 | `QuickLearners` | Experience Multiplier Trait |
| 81 | `Quartermaster` | Resource Per Flag Bonus Trait |
| 82 | `ScavengerTrait` | Scavenger Trait |

## Newly added traits (2026-10-17)

| traitId | Trait | Category shown in Unity |
| ---: | --- | --- |
| 78 | `HeavyATGun` | Passive Combat Bonus Trait |
| 79 | `ATGun` | Passive Combat Bonus Trait |
| 80 | `QuickLearners` | Experience Multiplier Trait |
| 81 | `Quartermaster` | Resource Per Flag Bonus Trait |
| 82 | `ScavengerTrait` | Scavenger Trait |

These names and indices are taken from the `TraitsConfig.Items` screenshot. The screenshot identifies the trait categories but **does not define exact gameplay numbers or restrictions**; check the in-game traits or game config for those values.

[Download machine-readable trait list (CSV)](traits.csv)
