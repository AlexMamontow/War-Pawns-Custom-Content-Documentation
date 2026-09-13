# Publishing to Steam Workshop

Use this after your mod works locally.

## Before publishing

Open War Pawns and check:

```text
Mods -> select your mod
```

The mod should show:

```text
Status: Valid
```

Then launch it from:

```text
Singleplayer -> Custom Scenarios
```

or:

```text
Singleplayer -> Custom Campaigns
```

Do not publish a mod if the Play button is disabled.

Checklist: [PUBLISHING_CHECKLIST.md](PUBLISHING_CHECKLIST.md)

## First publish

For a new local mod, `workshopId` in `manifest.json` should be empty or missing.

Example:

```json
"workshopId": ""
```

Open the `Mods` screen, select the mod, and press `Publish`.

After successful publishing, the game writes the Steam Workshop item ID into `manifest.json`.

## Updating an existing Workshop item

If `workshopId` exists, the `Update` button is used instead of `Publish`.

Example:

```json
"workshopId": "1234567890"
```

Make sure this ID belongs to the Workshop item you want to update.

## Validation errors

Invalid mods should not be published.

Fix validation errors first, then publish again.

Common blockers:

- wrong map reference
- missing entry file
- invalid JSON syntax
- scenario ID mismatch
- campaign mission path mismatch
- missing scenario graph
