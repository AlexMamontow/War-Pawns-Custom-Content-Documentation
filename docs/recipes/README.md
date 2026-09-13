# Scenario recipes

Recipes are copy-paste examples for common scenario logic.

Use them after your template already runs in game.

## Recommended order

1. [win_when_enemies_destroyed.md](win_when_enemies_destroyed.md)
2. [spawn_reinforcements.md](spawn_reinforcements.md)
3. [trigger_popup_when_unit_enters_zone.md](trigger_popup_when_unit_enters_zone.md)
4. [give_or_take_resources.md](give_or_take_resources.md)
5. [damage_or_heal_units_in_zone.md](damage_or_heal_units_in_zone.md)
6. [add_or_remove_unit_traits.md](add_or_remove_unit_traits.md)
7. [unlock_next_campaign_mission.md](unlock_next_campaign_mission.md)
8. [temporary_mission_completion_for_testing.md](temporary_mission_completion_for_testing.md)

## Before using a recipe

Check these references:

- maps: [../05_using_maps.md](../05_using_maps.md)
- IDs: [../06_using_ids.md](../06_using_ids.md)
- scenario reference: [../reference/SCENARIO_REFERENCE.md](../reference/SCENARIO_REFERENCE.md)

## Important

Most recipes use `payload` strings. Because `payload` is JSON inside JSON, quotation marks inside it must be escaped.

Example:

```json
"payload": "{"amount":5}"
```
