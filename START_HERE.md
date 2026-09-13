# Start here: run your first custom scenario

This guide shows how to run a working scenario template without editing anything.

Do this first. After the template works in game, change one thing at a time.

## What you need

- War Pawns installed
- A text editor such as VS Code, Notepad++, or any JSON-friendly editor
- This repository downloaded as ZIP

You do not need Unity.

## 1. Download the repository

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

If the folder does not exist, launch War Pawns once, open `Mods`, and press `Open Folder`.

## 3. Copy the scenario template

Copy this folder from the repository:

```text
templates/WarPawns_TemplateScenario
```

Paste it into:

```text
Documents/War Pawns/Mods/
```

The final path must be:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
```

## 4. Check for the most common mistake

Correct:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/manifest.json
```

Wrong:

```text
Documents/War Pawns/Mods/WarPawns_TemplateScenario/WarPawns_TemplateScenario/manifest.json
```

If the folder is nested twice, the game will not find the mod correctly.

## 5. Check the mod in game

Launch War Pawns.

Open:

```text
Mods
```

Select the template. It should show:

```text
Status: Valid
```

If it is `Invalid`, select the mod and read the validation messages. Then open [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md).

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

The Scenario Room opens before the match starts. You can choose difficulty and turn time there. By default, turn time is unlimited.

## 7. Make your first edit

After the template runs successfully, continue here:

```text
docs/02_creating_your_first_scenario.md
```

Do not start from an empty file. Start from the working template and edit one small thing at a time.

## Quick checklist

Before asking why a mod does not work, check these three things:

- Is `manifest.json` directly inside the mod folder?
- Does the mod show `Valid` in the `Mods` screen?
- Does the scenario use a correct built-in `map.id` or a real custom `map.path`?
