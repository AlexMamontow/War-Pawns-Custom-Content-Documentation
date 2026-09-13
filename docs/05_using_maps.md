# Using maps in custom scenarios

Every scenario needs a map.

There are two ways to set a map:

1. use a built-in War Pawns map ID
2. include your own `.map` file in the mod and reference it by path

Use only one of these in a scenario: `id` or `path`.

## Option 1 — use a built-in map

Use this when you want to build a scenario on one of the maps already included in War Pawns.

Example:

```json
"map": {
  "id": "afccd13f3a754d49aa010c63dc297084"
}
```

This uses the built-in Ardennes map.

All built-in map IDs are listed here:

[reference/BUILT_IN_MAPS.md](reference/BUILT_IN_MAPS.md)

## Option 2 — use your own custom map file

Put your map file inside the mod:

```text
MyMod/
  manifest.json
  scenarios/my_scenario.scenario
  maps/my_map.map
```

Then reference it like this:

```json
"map": {
  "path": "maps/my_map.map"
}
```

The path is relative to the mod folder.

## Do not use both id and path

Wrong:

```json
"map": {
  "id": "afccd13f3a754d49aa010c63dc297084",
  "path": "maps/my_map.map"
}
```

Correct built-in map:

```json
"map": {
  "id": "afccd13f3a754d49aa010c63dc297084"
}
```

Correct custom map:

```json
"map": {
  "path": "maps/my_map.map"
}
```

## Common mistake

This usually will not work:

```json
"map": {
  "id": "e1b457d2077e4237b00c481a6b50943b"
}
```

A map `id` must belong to a built-in map included in the game.

If the player created or exported their own map, the mod must include the `.map` file and use `path`.

## If Play is disabled

Check these first:

- Does `map.id` exist in [reference/BUILT_IN_MAPS.md](reference/BUILT_IN_MAPS.md)?
- If using `map.path`, does the file really exist in the mod folder?
- Did you use only one map reference, not both `id` and `path`?
- Are starting unit positions valid for this map?

More help: [TROUBLESHOOTING.md](TROUBLESHOOTING.md)
