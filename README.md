# QuestPlates (Archived)

> **Maintenance status:** QuestPlates is archived and no longer maintained. It has been superseded by [RGX | Simple Quest Plates](https://github.com/RGXMods/SimpleQuestPlates). Use the successor for current features, updates, and support.

QuestPlates is a Retail World of Warcraft nameplate addon originally created by Semlar and later updated by DonnieDice. It adds quest progress indicators to units that the client identifies as related to an active quest. This repository remains available as historical source and for existing installations; the details below describe the archived `v5.4.10` code.

## Behavior and Features

- Creates an overlay frame for each Blizzard nameplate and updates it as units appear, disappear, or their quest state changes.
- Shows a quest marker and the largest remaining numeric objective count found in unit-tooltip quest lines.
- Shows remaining percentage progress in cyan for percentage-based objectives.
- Adds a bag-style loot marker when an unfinished quest objective is an item or object interaction.
- Shows the quest-log special-item texture when one is available for the matched quest-log entry.
- Tracks active world quests on the player's current map and refreshes its quest cache when quests are accepted, removed, watched, or updated.
- Animates the quest marker when its overlay becomes visible.
- Suppresses its overlay during challenge-mode scenarios.
- Uses the bundled stripped SemlarPlates event/nameplate layer in `semlib/`; no separate nameplate library or addon is required.

QuestPlates reads quest details from client tooltip and quest APIs. Its output therefore depends on what the game exposes for the visible unit and active quest; an eligible objective may not produce an icon when those APIs provide no matching progress text.

## Compatibility and Metadata

The only TOC is `QuestPlates.toc`:

| Field | Current value |
| --- | --- |
| Version | `v5.4.10` |
| Interface | `120007` |
| Client scope | Retail only |
| SavedVariables | `QuestPlateSettings` |
| Required dependencies | None |
| Package directory | `QuestPlates` |

No Classic interface is declared in this archived branch. The addon loads `semlib/semlib.xml` before `QuestPlates.lua`.

## Installation

Because the project is archived, new users should install [RGX | Simple Quest Plates](https://www.curseforge.com/wow/addons/simple-quest-plates) instead.

To inspect or run this archived version manually:

1. Download a source archive from the configured downstream repository, [DonnieDice/QuestPlates](https://github.com/DonnieDice/QuestPlates).
2. Extract it to `World of Warcraft/_retail_/Interface/AddOns`.
3. Ensure the final path is `Interface/AddOns/QuestPlates/QuestPlates.toc`, without an extra repository-name directory level.
4. Restart WoW, enable QuestPlates in the AddOns list, and allow out-of-date addons only if the installed client requires it.

## Usage and Configuration

QuestPlates works automatically after login. It has no addon slash command and no options panel. The archived source exposes five values through the global `QuestPlateSettings` table:

| Setting | Default | Purpose |
| --- | --- | --- |
| `AnchorPoint` | `RIGHT` | Point on the quest icon attached to the nameplate overlay. |
| `RelativeTo` | `LEFT` | Point on the overlay to which the icon is attached. |
| `OffsetX` | `0` | Horizontal offset in pixels. |
| `OffsetY` | `0` | Vertical offset in pixels. |
| `IconScale` | `1` | Scale applied to the complete quest overlay. |

The source comments document changing these values with WoW's `/run` command. For example:

```text
/run QuestPlateSettings.OffsetX = -10; QuestPlateSettings.OffsetY = 5
/run QuestPlateSettings.AnchorPoint = 'LEFT'; QuestPlateSettings.RelativeTo = 'RIGHT'
/reload
```

To request the defaults again:

```text
/run QuestPlateSettings = nil
/reload
```

This is legacy source-level configuration, not a supported settings interface. The archived Lua initializes the settings table with defaults while loading, so verify custom values after a reload rather than assuming they persist as expected on current clients.

## Troubleshooting

- If no icons appear, confirm that enemy nameplates are enabled, the unit is related to one of the character's active quests, and the unit tooltip contains objective progress the addon can parse.
- QuestPlates intentionally hides its overlays during challenge-mode scenarios.
- If the addon is missing from the AddOns list, verify the folder path and that `QuestPlates.toc` is directly inside the `QuestPlates` directory.
- If Retail reports the addon as out of date, compare the client's interface number with the archived TOC value `120007`. This archive does not promise updates for newer clients.
- If custom positioning does not survive reload, reset to defaults and use the maintained successor's supported configuration UI instead.
- Lua errors from newer game APIs are not evidence of active support; this repository is retained as an archive.

## History and Successor

The repository identifies Semlar and DonnieDice as authors, and the bundled nameplate layer describes itself as a stripped core from SemlarPlates. The historical changelog records fixes for world-quest ID handling, tooltip API guards, quest event updates, and icon reanchoring before the final Retail TOC update.

- [Archived change history](docs/changelog.txt)
- [Current archived release notes](docs/CHANGES.md)
- [Archived downstream repository](https://github.com/DonnieDice/QuestPlates)
- [Maintained successor source](https://github.com/DonnieDice/RGX_SimpleQuestPlates)
- [Maintained successor download](https://www.curseforge.com/wow/addons/rgx-simplequestplates)

Please direct current feature requests and support questions to the successor project. This archived repository should not be presented as actively maintained.
