# KitsuneZombieReach

**Shortens zombie melee reach in 7 Days to Die so hits land closer to where the zombie actually is.**

7D2D 2.x zombies have melee ranges between 1.3m and 1.75m. Combined with server/client desync, that produces the "how did they hit me from over there" feeling. This mod tightens horizontal reach on every zombie hand item — including the new Rancher and Chuck zombies — while nerfing crawlers a little further since they're low to the ground anyway.

This is a horizontal-reach adjustment only. Vertical reach (zombies hitting from above/below) is a separate code path and not touched by this mod.

## Requirements

- 7 Days to Die V2.0+
- **Server-side only.** Install on the server (or in single player). Clients do not need it.
- EAC can stay enabled; this is a pure XML config patch.

## Installation

1. Drop the `KitsuneZombieReach` folder from the release zip into your `Mods/` folder on the server.
2. Restart the server.

That's it. No DLL, no Harmony, no client install.

## What it patches

All values are in meters. "Vanilla" is the stock 2.x value for that item; "Mod" is what this mod sets it to.

| Zombie group | Items | Vanilla | Mod |
|---|---|---:|---:|
| Standard walkers | `meleeHandMaster`, `meleeHandZombie01`, `meleeHandZombieShort`, `meleeHandZombieShortFeral`, `meleeHandZombieBurning`, `meleeHandZombieBurningFeral` | 1.4 – 1.65 | **1.375** |
| Large zombies (Cop, Mutated ×5, Rancher, Chuck) | `meleeHandZombieCop`, `meleeHandzombieMutated` + Feral/Radiated/Charged/Infernal, `meleeHandZombieRancher`, `meleeHandZombieChuck` | 1.7 – 1.75 | **1.55** |
| Crawlers | `meleeHandZombie02`, `meleeHandZombie02Feral`, `meleeHandZombieBurningCrawler` | 1.3 | **1.2** |

`Extends` chains mean Feral/Charged/Infernal variants that don't override `Range` inherit from their parent, so patching the parent covers them automatically. Rancher, Chuck, Cop, and Mutated variants all cascade this way.

## What it does NOT touch

- `meleeHandZombieStrong` / `Demolition` (3.1m shoulder charge — intentional)
- `meleeHandZombieBoar` (2.2m, animal AI)
- `meleeHandZombieWorker`, `HazMat`, `PartyGirl` variants — left at vanilla

## Credits

Inspired by [KhaineGB's Zombie Reach Adjustment](https://www.nexusmods.com/7daystodie) — the idea of tightening zombie reach to make melee feel fair is his. Values and item list in this mod are our own (researched against current 2.x `items.xml`), and coverage has been extended to include the new Rancher and Chuck zombies plus crawlers, which the original doesn't cover.

Made by AdaInTheLab.
