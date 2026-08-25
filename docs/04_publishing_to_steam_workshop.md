# 04 — Publishing to Steam Workshop

Use the in-game `Mods` screen to publish or update local custom content.

## Before publishing

Check:

- the mod status is `Valid`
- `manifest.json` has a unique `id`
- `scenarioId` or `campaignId` is unique
- `workshopId` is empty for a new item
- preview image exists, if you set `preview`
- the template/debug test conditions were removed

## Publish a new mod

1. Open War Pawns.
2. Open `Mods`.
3. Select your local mod.
4. Press `Publish`.
5. After successful publish, the game writes the Steam Workshop item ID into `manifest.json` as `workshopId`.

After this, `Publish` becomes disabled and `Update` becomes available.

## Update an existing Workshop item

If `manifest.json` already has `workshopId`, press:

```text
Update
```

Do not press `Publish` unless you intentionally want a new Workshop item and have cleared `workshopId`.

## Visibility

A newly published Workshop item may be hidden/private depending on Steam settings. Open the Workshop page and set visibility as needed.

## Common Steam issues

See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for errors such as AccessDenied, InvalidParam, or 0-byte uploaded content.

