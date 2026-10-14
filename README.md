# SkyGamble loot pools

SkyFortune loads the Zombie Slayer pool from [`loot-pools/zombie_slayer.json`](loot-pools/zombie_slayer.json).

To publish a change, edit that JSON and increase its integer `version` field (`1` → `2` → `3` ...). Clients check for a newer version when entering a world and about every 30 minutes while playing. `/skyfortune update` checks immediately. Only the loot pool changes; updating the mod JAR is separate.

The client keeps a backup of its previous JSON and rejects invalid data. Custom head profiles already captured locally are retained when an updated entry has no `profile` field.
