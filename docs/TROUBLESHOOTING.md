# Troubleshooting

## My mod does not appear in the Mods screen

Check the folder layout.

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
- `manifest.json` is valid JSON
- `contentType` is either `Scenario` or `Campaign`
- the `entry` file exists

## My mod is Invalid

Open `Mods`, select your mod, and read the validation messages.

Common causes:

- wrong `contentType`
- missing `entry`
- `scenarioId` mismatch between `manifest.json` and `.scenario`
- `campaignId` mismatch between `manifest.json` and `.campaign`
- invalid map ID
- invalid JSON syntax
- unknown trigger, condition, action, or command
- missing scenario file referenced by a campaign

## The scenario starts and instantly ends

Usually the win condition is already true at scenario start.

Example:

- win condition says `NoUnitsMatch` for enemy units
- enemy units failed to spawn because of invalid player, unit, nation, or coordinate
- therefore the game sees no enemies and ends the mission immediately

Check:

- enemy `initialUnits` exist
- enemy `ownerPlayerId` exists in `players`
- enemy `unitDataId` exists for that player's `nationId`
- enemy position is a valid cube coordinate on the selected map

## The game shows raw localization keys

If the UI shows something like:

```text
my_mod.popup.title
```

then the key is missing from `localization/en.json` or the localization file is not listed in `manifest.json`.

Check:

```json
"localization": [
  { "language": "en", "path": "localization/en.json" }
]
```

## A popup appears without image

Check that the thumbnail path is relative to the mod root:

```json
"thumbnail": "images/popup_thumbnail.png"
```

Do not use an absolute path.

## Spawned unit does not appear

Check:

- `ownerPlayerId` exists
- `unitDataId` exists for the owner's nation
- the target coordinate is valid
- the map is loaded correctly

If the requested spawn hex is occupied, the game tries to use the nearest available hex. If no valid hex is available, the unit is skipped with a warning.

## Unit selector affects no units

Empty selectors match no units.

Use `allUnits: true` only when you intentionally want all units.

Example:

```json
"targets": {
  "allUnits": true,
  "aliveOnly": true,
  "teamIds": [1]
}
```

## JSON does not load

JSON does not support comments, trailing commas, or unescaped quotes inside strings.

Bad:

```json
{
  "type": "SendCommand",
  "payload": "{"playerId":0,"amount":3}"
}
```

Good:

```json
{
  "type": "SendCommand",
  "payload": "{"playerId":0,"amount":3}"
}
```

## Steam Workshop item uploads as 0 bytes

Check Steamworks setup for the app. Workshop file transfer must be enabled for `SetItemContent` / `SubmitItemUpdate` uploads to work.

## Steam Workshop AccessDenied

Usually this means Steam denied the operation for the current app/account/build.

Check:

- the game is running under the correct Steam AppID
- the account has access to the app
- Workshop is enabled for the app
- the Steam Workshop legal agreement has been accepted if Steam asks for it

## Steam Workshop InvalidParam

Check:

- title is not empty
- description is not invalid/too long
- content folder exists
- preview path exists if preview is set
- `workshopId` belongs to an existing item when updating

