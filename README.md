# SkyGamble configs for SkyFortune

- `loot-pools/{zombie,spider,wolf,enderman,vampire,blaze}_slayer.json` controls each Slayer roll pool: item IDs, names, icons, card colors, head skins, `settingsSlot`, `settingsLore`, and optional `chancePercent` for each drop.
- [`ui/settings.json`](ui/settings.json) controls the Slayer settings inventories: titles, row counts, serialized item stacks, labels, action slots and drop positions.

Both files have their own integer `version`. Increase only the version of the file you changed (`1` → `2` → `3` ...). SkyFortune checks for newer versions when entering a world and about every 30 minutes while playing. `/skyfortune update` checks immediately. The client saves a backup before replacing a local JSON.

In `ui/settings.json`, `pages.selector` is the Slayer selection screen and `pages.<slayer>` is that Slayer's drop screen. Each `slots` array contains one serialized Minecraft item stack per inventory position; `null` means empty. `actions` maps click behavior to slot numbers. `dropSlots` maps loot item IDs to positions on the corresponding Slayer page. The visible drops come from the current loot pool, so removing a drop there also removes it from the settings inventory. A new drop without a `settingsSlot` or `dropSlots` entry is placed in the first free interior slot. To choose its exact position or tooltip, edit the UI JSON too and increase its version.

The new Slayer pools contain approximate highest-tier baseline chances from [skyblock-rng-optimizer](https://github.com/kyotinho/skyblock-rng-optimizer); `chanceApproximate: true` displays a `~` prefix. Lower-tier odds can differ. The roll always stops on the server-announced item. Standard guaranteed Slayer materials are excluded from the roll pools.

The mod JAR itself is updated separately.
