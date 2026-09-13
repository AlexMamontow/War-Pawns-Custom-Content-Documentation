# Publishing checklist

Before publishing or updating a mod on Steam Workshop, check this list.

## Required

- The mod appears in the `Mods` screen.
- Status is `Valid`.
- `manifest.json` is directly inside the mod folder.
- `contentType` is correct: `Scenario` or `Campaign`.
- `entry` points to an existing `.scenario` or `.campaign` file.
- The scenario uses a valid built-in `map.id` or a real custom `map.path`.
- The scenario can be launched from `Singleplayer -> Custom Scenarios` or from its campaign.
- The mission does not instantly complete unless this is intentional.
- Temporary testing win conditions were removed.

## Recommended

- `titleKey` and `descriptionKey` resolve to readable text.
- Preview image exists.
- Campaign missions have readable titles and descriptions.
- `workshopId` is empty for first publish.
- `workshopId` is set only when updating an existing Workshop item.

## Do not publish

Do not publish a mod if:

- it is `Invalid`
- the Play button is disabled
- the map cannot be loaded
- enemy units fail to spawn
- the mission immediately ends by accident
