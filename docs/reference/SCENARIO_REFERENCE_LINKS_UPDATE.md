# Scenario Reference Update

Add these links to `docs/reference/SCENARIO_REFERENCE.md` or to the main reference index:

- [Unit traits](TRAITS.md)
- [Unit actions](UNIT_ACTIONS.md)

Important distinction:

- **Scenario actions** are graph actions executed by the scenario runner, for example `SendCommand`, `EndMission`, `ShowRegularPopup`, or `HighlightZone`.
- **Unit actions** are gameplay actions available to units, for example `MovementAction`, `AttackAction`, `Raid`, `ReconAreaAction`, or `OfficerEncourageAction`.

When editing custom scenario JSON, use scenario actions inside the scenario graph. Use unit action IDs only in payloads that explicitly ask for unit actions.
