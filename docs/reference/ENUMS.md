# Enums and common IDs

## Teams

| teamId | Meaning |
| --- | --- |
| 0 | Team A / player side by convention |
| 1 | Team B / enemy side by convention |
| 2 | Observer |

## Nations

| nationId | Nation |
| --- | --- |
| 0 | Germany |
| 1 | USSR |
| 2 | Britain |
| 3 | USA |
| 4 | Japan |

## Unit types

Use string names in `unitTypes` selectors when possible. Use `unitTypeIds` only if you specifically want numeric enum values.

| unitTypeId | UnitType name |
| --- | --- |
| 0 | Officer |
| 1 | Infantry |
| 2 | Tank |
| 3 | SpecialInfantry |
| 4 | Vehicle |
| 5 | Artillery |
| 6 | SpecialVehicle |
| 7 | SelfPropelledArtillery |
| 8 | SupportInfantry |

## Player IDs

`playerId` comes from the scenario `players` array. For scenario logic, prefer `teamIds` where possible because they are usually more stable for ally/enemy logic.
