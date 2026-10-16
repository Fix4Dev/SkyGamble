# SkyGamble configs for SkyFortune

- `loot-pools/{zombie,spider,wolf,enderman,vampire,blaze}_slayer.json` controls each Slayer roll pool: item IDs, names, icons, card colors, head skins, `settingsSlot`, `settingsLore`, and optional `chancePercent` for each drop.
- [`ui/settings.json`](ui/settings.json) controls the Slayer settings inventories: titles, row counts, serialized item stacks, labels, action slots and drop positions.
- [`dungeons/m5.json`](dungeons/m5.json) controls the Master Mode Floor V roll candidates for Croesus's Obsidian and Bedrock chests. `minimumChest` is the first chest tier shown by Hypixel's RNG Meter; later tiers can contain the same item. The saved odds are the values displayed in the captured M5 RNG Meter, not verified per-chest probabilities. The roll result is selected from the actual contents in the Croesus chest tooltip. If no listed RNG item matches, the roll shows an ordinary item from that chest instead.

Each file has its own integer `version`. Increase only the version of the file you changed (`1` → `2` → `3` ...). SkyFortune checks for newer versions when entering a world and about every 30 minutes while playing. `/skyfortune update` checks immediately. The client saves a backup before replacing a local JSON.

In `ui/settings.json`, `pages.selector` is the Slayer selection screen and `pages.<slayer>` is that Slayer's drop screen. Each `slots` array contains one serialized Minecraft item stack per inventory position; `null` means empty. `actions` maps click behavior to slot numbers. `dropSlots` maps loot item IDs to positions on the corresponding Slayer page. The visible drops come from the current loot pool, so removing a drop there also removes it from the settings inventory. A new drop without a `settingsSlot` or `dropSlots` entry is placed in the first free interior slot. To choose its exact position or tooltip, edit the UI JSON too and increase its version.

Spider, Wolf and Enderman slots, icons and odds are taken from captured Hypixel RNG Meter inventories. Their odds reflect the captured tier and may change on the server. Vampire and Blaze are shown as „Noch nicht verfügbar“ and do not open a settings page or trigger rolls. The remaining approximate values use `chanceApproximate: true` to display `~`. The roll always stops on the server-announced item. Standard guaranteed Slayer materials are excluded from the roll pools.

The mod JAR itself is updated separately.
