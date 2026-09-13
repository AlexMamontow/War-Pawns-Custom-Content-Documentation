# Coordinates

For choosing a map, see [../05_using_maps.md](../05_using_maps.md).


War Pawns uses cube hex coordinates in JSON:

```json
{ "x": 4, "y": -4, "z": 0 }
```

For valid cube coordinates, `x + y + z = 0`. For example, `{ "x": 4, "y": 0, "z": -4 }` is not valid for the standard maps in this documentation; use `{ "x": 4, "y": -4, "z": 0 }` instead.

All public built-in maps listed in `BUILT_IN_MAPS.md` use the same 256 coordinate positions:

- X range: `-7..15`
- Y range: `-23..0`
- Z range: `0..15`

The complete coordinate list is available in [`standard_map_coordinates.csv`](standard_map_coordinates.csv).

Practical advice:

- Use coordinates from the map editor when possible.
- When spawning units, pick a coordinate that exists on the selected map.
- If a spawn coordinate is occupied, `spawn_units` searches for the nearest available map hex.
- Coordinate existence does not guarantee that the terrain is tactically useful or passable for every unit type.
