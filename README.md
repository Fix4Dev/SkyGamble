# SkyGamble configs for SkyFortune

- [`loot-pools/zombie_slayer.json`](loot-pools/zombie_slayer.json) controls the Zombie Slayer roll pool: item IDs, names, icons, card colors, head skins, `settingsSlot` and `settingsLore` for each drop.
- [`ui/settings.json`](ui/settings.json) controls the Slayer settings inventories: titles, row counts, serialized item stacks, labels, action slots and drop positions.

Both files have their own integer `version`. Increase only the version of the file you changed (`1` → `2` → `3` ...). SkyFortune checks for newer versions when entering a world and about every 30 minutes while playing. `/skyfortune update` checks immediately. The client saves a backup before replacing a local JSON.

In `ui/settings.json`, `pages.selector` is the Slayer selection screen and `pages.zombie` is the Zombie drop screen. Each `slots` array contains one serialized Minecraft item stack per inventory position; `null` means empty. `actions` maps click behavior to slot numbers. `dropSlots` maps loot item IDs to Zombie-page positions. The visible drops come from the current loot pool, so removing a drop there also removes it from the settings inventory. A new drop without a `settingsSlot` or `dropSlots` entry is placed in the first free interior slot. To choose its exact position or tooltip, edit the UI JSON too and increase its version.

The mod JAR itself is updated separately.
