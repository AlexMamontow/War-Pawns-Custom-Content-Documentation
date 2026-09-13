# Troubleshooting

Use this page when a mod appears in game but does not work as expected.

## My mod does not appear in the Mods screen

Check the folder structure.

Correct:

```text
Documents/War Pawns/Mods/MyMod/manifest.json
```

Wrong:

```text
Documents/War Pawns/Mods/MyMod/MyMod/manifest.json
```

Also check:

- the file is named exactly `manifest.json`
- the mod is inside `Documents/War Pawns/Mods/`
- the repository ZIP was unzipped before copying

## My mod is Invalid

Open `Mods`, select your mod, and read the validation messages.

Common causes:

- invalid JSON syntax
- missing `manifest.json`
- wrong `contentType`
- missing `entry`
- entry file does not exist
- manifest `scenarioId` does not match the `.scenario` file
- manifest `campaignId` does not match the `.campaign` file
- campaign mission path is wrong
- scenario map is missing
- scenario graph is missing

## Play button is disabled

This usually means the game can see the mod, but the selected scenario cannot be launched.

Check:

1. Is the mod `Valid` in the `Mods` screen?
2. Does the scenario have a valid map?
3. Does the scenario have a scenario graph with an entry step and main objective?
4. Does the scenario have players?
5. If this is a campaign mission, is it locked by `requiredScenarioIds`?

The most common map problem:

```json
"map": {
  "id": "some_custom_map_id"
}
```

This works only if `some_custom_map_id` is a built-in map ID included in the game.

For custom map files, use:

```json
"map": {
  "path": "maps/my_map.map"
}
```

and make sure the mod contains:

```text
maps/my_map.map
```

Full map guide: [05_using_maps.md](05_using_maps.md)

## The scenario starts and instantly ends

Usually the win condition is already true at scenario start.

Example:

- win condition says no enemy units remain
- enemy units failed to spawn
- therefore the mission immediately completes

Check the console and validation messages for failed unit spawns.

Common causes:

- invalid `ownerPlayerId`
- invalid `unitDataId`
- invalid unit position
- wrong map
- no enemy units in `initialUnits`

## A unit does not spawn

Check:

- `ownerPlayerId` exists in `players`
- `unitDataId` exists for that player's `nationId`
- the target `position` exists on the selected map
- the target position is not blocked in a way that prevents spawning

Cube coordinates should usually follow:

```text
x + y + z = 0
```

Example:

```json
"position": { "x": 4, "y": -12, "z": 8 }
```

## Text shows as a key instead of readable text

Example problem:

```text
my_mod.mission_01.title
```

This means the localization key was not found.

Check `localization/en.json` and make sure the key exists:

```json
{
  "key": "my_mod.mission_01.title",
  "path": "Mission 1"
}
```

Also check that `manifest.json` includes the localization file:

```json
"localization": [
  { "language": "en", "path": "localization/en.json" }
]
```

## My popup has no image

Check:

- the image path is relative to the mod folder
- the file exists
- the file is a readable image format

Example:

```json
"thumbnail": "images/popup_thumbnail.png"
```

Expected file:

```text
MyMod/images/popup_thumbnail.png
```

## JSON error after editing

JSON is strict.

Common mistakes:

- comments are not allowed
- missing comma between fields
- trailing comma after the last item
- unescaped quotation marks inside `payload`

When editing `payload`, remember that it is a JSON string inside JSON, so internal quotes must be escaped.

Example:

```json
"payload": "{"amount":5}"
```

## Steam Workshop upload is blocked

Invalid mods should not be published.

Check the mod in the `Mods` screen first. It should be `Valid` before publishing.

Warnings can be acceptable, but validation errors should be fixed before upload.
