# War Pawns Custom Content Starter Kit

Create custom scenarios and campaigns for **War Pawns**.

You do **not** need Unity. You only need the game, a text editor, and one of the templates in this repository.

## Start with this goal

Before editing anything, get a working template running in the game.

1. Click `Code -> Download ZIP` on GitHub.
2. Unzip the repository.
3. Copy this folder:

   ```text
   templates/WarPawns_TemplateScenario
   ```

   to:

   ```text
   Documents/War Pawns/Mods/
   ```

4. The final path must be:

   ```text
   Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
   ```

5. Launch War Pawns.
6. Open `Mods` and check that the template is `Valid`.
7. Open `Singleplayer -> Custom Scenarios` and press `Play`.

Full walkthrough: [START_HERE.md](START_HERE.md)

## What do you want to do?

| Goal | Open this |
| --- | --- |
| Run your first template | [START_HERE.md](START_HERE.md) |
| Install a template correctly | [docs/01_installing_a_template.md](docs/01_installing_a_template.md) |
| Make your first standalone scenario | [docs/02_creating_your_first_scenario.md](docs/02_creating_your_first_scenario.md) |
| Make a two-mission campaign | [docs/03_creating_your_first_campaign.md](docs/03_creating_your_first_campaign.md) |
| Use a built-in map or custom map | [docs/05_using_maps.md](docs/05_using_maps.md) |
| Understand IDs for units, traits, actions, teams, nations | [docs/06_using_ids.md](docs/06_using_ids.md) |
| Publish or update on Steam Workshop | [docs/04_publishing_to_steam_workshop.md](docs/04_publishing_to_steam_workshop.md) |
| Fix common problems | [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) |
| Copy ready-made scenario logic | [docs/recipes/](docs/recipes/) |
| Look up all technical IDs and schemas | [docs/reference/](docs/reference/) |

## Templates

| Template | Use it for |
| --- | --- |
| `templates/WarPawns_TemplateScenario` | One standalone custom scenario |
| `templates/WarPawns_TemplateCampaign` | A campaign with two linked missions |

Always start from a template. Writing a `.scenario` file from scratch is possible, but it is not recommended for a first mod.

## How a mod folder works

A simple standalone scenario looks like this:

```text
MyMod/
  manifest.json
  scenarios/my_scenario.scenario
  localization/en.json
  images/preview.png
```

A campaign looks like this:

```text
MyCampaignMod/
  manifest.json
  campaigns/my_campaign.campaign
  scenarios/mission_01.scenario
  scenarios/mission_02.scenario
  localization/en.json
  images/preview.png
```

The `manifest.json` file tells the game what this mod is and which file should be loaded first.

## Very important rules

- `manifest.json` must be directly inside the mod folder.
- One mod folder equals one playable entry: either one standalone scenario or one campaign.
- JSON files do not support comments.
- Use globally unique IDs such as `my_mod.mission_01`.
- Keep `workshopId` empty for a new local mod.
- For maps, use either a built-in `map.id` or a custom `map.path`, not both.
- Use `payload`, not `key`, in JSON scenario actions.
- The Scenario Room turn-time dropdown defaults to no turn timer. Dropdown item `0` means unlimited turn time.

## Where is the full reference?

The beginner guides are in `docs/`.

The technical reference is in `docs/reference/`.

Start with the guides first. Use the reference only when you need a specific map ID, unit ID, trait ID, action ID, enum value, trigger, condition, or payload field.
