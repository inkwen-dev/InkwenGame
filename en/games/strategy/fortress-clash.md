# Fortress Clash

<a href="https://inkwengame.com/games/fortress-clash" target="_blank" rel="noopener noreferrer">Play on InkwenGame</a>

![cover](https://img.inkwengame.com/games/fortress-clash/cover.jpg)

Fixed the reported issue: progress was not restored after a reload.

## How to play

Pick a block or unit from the bottom tray, then tap the grid to place it on your cart and build your fort and army. Blocks cost coins; every win pays out coins and lets you choose a bonus reward. Press Battle to launch - your archers and units fire at the enemy fort automatically. Win by destroying the enemy king: knock him off his cart, bury him in rubble, or blast through his walls. Spend coins on the Upgrade screen to level up units and unlock new weapons (cannon, crossbow, laser, grenade). Play with mouse or touch - no keyboard needed.

## About

Fixed the reported issue: progress was not restored after a reload.

Root cause: bridge.storage.get() returns the saved value already parsed as an object, while the game expected a JSON string and parsed it again, which threw and silently discarded the save.

Changes:
- storage.get() now accepts both shapes (object and string).
- The save is loaded BEFORE gameplay is shown: a loading screen is displayed and input is ignored until storage.get() resolves, so a fresh default save can no longer overwrite real progress during startup.
- Saves carry a revision counter, so after "finish a level, then buy an upgrade" the newest copy always wins instead of an older one at the same level.
- Any pending write is flushed on page hide / unload, so the last action before a reload is never lost.

Verified in the QA tool: state written before Reload game is fully restored after it.

## Details

- Category: <a href="https://inkwengame.com/strategy" target="_blank" rel="noopener noreferrer">Strategy</a>
- Orientation: portrait
- Plays on: desktop, mobile
- Game language: en
- Developer: Playgama
- Tags: strategy, Tower Defense
