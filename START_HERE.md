# Start here: run your first custom scenario

This guide shows how to run a working custom scenario template without editing anything.

Do this first. After the template works in game, you can safely start changing IDs, text, units, objectives, and triggers.

## 1. Download this repository

On GitHub, click:

```text
Code -> Download ZIP
```

Unzip the downloaded archive somewhere easy to find.

## 2. Open the War Pawns Mods folder

The local mods folder is:

```text
Documents/War Pawns/Mods/
```

If you do not see this folder, launch War Pawns once, open `Mods`, and use the `Open Folder` button.

## 3. Copy the standalone scenario template

Copy this folder from the repository:

```text
templates/WarPawns_TemplateScenario
```

Paste it here:

```text
Documents/War Pawns/Mods/
```

The final folder should look like this:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
Documents/War Pawns/Mods/WarPawns_TemplateScenario/scenarios/template_scenario.scenario
Documents/War Pawns/Mods/WarPawns_TemplateScenario/localization/en.json
```

## 4. Avoid the most common install mistake

Correct:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
```

Wrong:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/WarPawns_TemplateScenario/manifest.json
```

If the mod folder is nested twice, the game will not find it.

## 5. Check the template in game

Launch War Pawns.

Open:

```text
Mods
```

You should see:

```text
Template Standalone Scenario
```

Its status should be:

```text
Valid
```

If it is `Invalid`, select the mod and read the validation messages. See [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md).

## 6. Play the template

Open:

```text
Singleplayer -> Custom Scenarios
```

Select:

```text
Template Scenario
```

Press:

```text
Play
```

The Scenario Room opens before the match starts. You can choose difficulty and turn time there. By default, turn time is unlimited. Dropdown item `0` means no turn timer.

## 7. Make your first edit

After the template runs successfully, continue here:

```text
docs/02_creating_your_first_scenario.md
```

Do not start by writing a scenario from scratch. Start from the working template and change one thing at a time.

