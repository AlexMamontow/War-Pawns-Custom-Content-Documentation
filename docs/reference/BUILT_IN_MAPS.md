# Built-in map IDs

Use these IDs in a scenario map block:

```json
"map": { "id": "afccd13f3a754d49aa010c63dc297084" }
```

The tutorial map is intentionally not included as a recommended public template map.

| Map | map.id | camouflageProfile | Tiles | X range | Y range | Z range |
| --- | --- | --- | --- | --- | --- | --- |
| Ardennes | afccd13f3a754d49aa010c63dc297084 | Regular | 256 | -7..15 | -23..0 | 0..15 |
| Bastogne | 783ec03b3de745798397af1926acbc29 | Winter | 256 | -7..15 | -23..0 | 0..15 |
| Cherbourg | 816212df57be4ff3ba1c8b301392bfeb | Regular | 256 | -7..15 | -23..0 | 0..15 |
| D-Day | 8721cf600ecc41afae64025f6f7c3c1f | Regular | 256 | -7..15 | -23..0 | 0..15 |
| Desert | 4879ffb5e6084ca69de42748774ce7b7 | Desert | 256 | -7..15 | -23..0 | 0..15 |
| Forests | 283a9afb960a45e1aa2d3eccf4d313d3 | Regular | 256 | -7..15 | -23..0 | 0..15 |
| Leipzig | 6b321e88c6b94627a3e4a2d38975af72 | Regular | 256 | -7..15 | -23..0 | 0..15 |
| Remagen | 2e26fe58433c46018eb09850d6f278fe | Regular | 256 | -7..15 | -23..0 | 0..15 |
| Ruhr | 1ae6f8f07c894dc69a73cd866839b382 | Regular | 256 | -7..15 | -23..0 | 0..15 |
| Stoneville | 58893908bca24292aab1d45de9d1325b | Winter | 256 | -7..15 | -23..0 | 0..15 |

All listed maps use the same 256 cube-coordinate grid. Terrain, movement cost, details, and tile traits differ by map.


## Important

Do not invent map IDs. A `map.id` works only if it is one of the built-in IDs listed on this page.

For a custom map file, use `map.path` instead, for example:

```json
"map": {
  "path": "maps/my_map.map"
}
```

Full guide: [../05_using_maps.md](../05_using_maps.md)
