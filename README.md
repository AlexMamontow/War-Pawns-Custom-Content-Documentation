# War Pawns Custom Content Documentation

Create and share custom scenarios and campaigns for **War Pawns**.

You do **not** need Unity. You only need:

- War Pawns installed
- a text editor such as VS Code, Notepad++, or any JSON-friendly editor
- one of the working templates in this repository

## New to War Pawns modding?

Start here: **[START_HERE.md](START_HERE.md)**

That guide shows how to copy a ready-made template into the game and run it without editing anything first.

## Fast path

1. Download this repository as ZIP.
2. Copy `templates/WarPawns_TemplateScenario` to:

   ```text
   Documents/War Pawns/Mods/WarPawns_TemplateScenario
   ```

3. Make sure the final path is:

   ```text
   Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
   ```

4. Launch War Pawns.
5. Open `Mods` and check that the template is `Valid`.
6. Go to `Singleplayer -> Custom Scenarios`.
7. Select `Template Scenario` and press `Play`.

## What should I read next?

| Goal | Read this |
| --- | --- |
| Run a template for the first time | [START_HERE.md](START_HERE.md) |
| Install a template correctly | [docs/01_installing_a_template.md](docs/01_installing_a_template.md) |
| Make your first scenario | [docs/02_creating_your_first_scenario.md](docs/02_creating_your_first_scenario.md) |
| Make a two-mission campaign | [docs/03_creating_your_first_campaign.md](docs/03_creating_your_first_campaign.md) |
| Publish/update a mod on Steam Workshop | [docs/04_publishing_to_steam_workshop.md](docs/04_publishing_to_steam_workshop.md) |
| Fix common errors | [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) |
| Copy common scenario logic | [docs/recipes/](docs/recipes/) |
| Look up map, unit, trait, action, and enum IDs | [docs/reference/](docs/reference/) |

## Templates

| Template | Use it for |
| --- | --- |
| `templates/WarPawns_TemplateScenario` | One standalone custom scenario |
| `templates/WarPawns_TemplateCampaign` | A campaign with two linked missions |

Always start by copying a template. Writing a `.scenario` file from scratch is possible, but not recommended for your first mod.

## Repository layout

```text
README.md
START_HERE.md
docs/
  01_installing_a_template.md
  02_creating_your_first_scenario.md
  03_creating_your_first_campaign.md
  04_publishing_to_steam_workshop.md
  TROUBLESHOOTING.md
  recipes/
  reference/
templates/
  WarPawns_TemplateScenario/
  WarPawns_TemplateCampaign/
```

## Important rules

- One mod folder equals one playable entry: either one standalone scenario or one campaign.
- `manifest.json` must be directly inside the mod folder.
- JSON does not support comments.
- Use globally unique IDs such as `my_mod.mission_01`.
- Keep `workshopId` empty for a new local mod.
- Use `payload`, not `key`, in JSON scenario actions.
- The Scenario Room turn-time dropdown defaults to no turn timer. Dropdown item `0` means unlimited turn time.

