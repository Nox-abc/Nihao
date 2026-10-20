# Blockcraft — a Minecraft-style voxel sandbox in one HTML file

**Download [`minecraft.html`](minecraft.html) and open it in a browser. That's it.**
No install, no server, no build step: the whole game is a single self-contained file
(WebGL2 + JavaScript). It works offline once downloaded.

> Fan-made recreation inspired by Minecraft Java Edition 1.21. Not affiliated with
> Mojang or Microsoft. All textures, models, sounds and music are generated
> procedurally in code at startup, so the file contains no copyrighted game assets.

## How to play

1. Download `minecraft.html` (on GitHub: open the file, then click **Download raw file**).
2. Double-click it to open it in Chrome, Edge, Firefox or Safari (any browser with WebGL2).
3. Click **Singleplayer** to create or load a world, or **Quick Play** for a random world.
4. Click inside the game to capture the mouse.

Worlds are saved automatically in your browser (IndexedDB).

### Controls

| Key | Action |
| --- | --- |
| W A S D | Move |
| Space | Jump / swim up (double-tap: toggle flight in creative) |
| Shift | Sneak / fly down |
| Ctrl or double-tap W | Sprint |
| Left click (hold) | Break block / attack |
| Right click | Place block / use / eat |
| Middle click | Pick block |
| 1–9 / mouse wheel | Select hotbar slot |
| E | Inventory (creative menu in creative mode) |
| Q / Ctrl+Q | Drop item / drop stack |
| T or / | Chat and commands |
| F1 / F2 / F3 / F5 | Hide HUD / screenshot / debug screen / camera perspective |
| Esc | Pause menu |

**Touch screens** (phones/tablets) get on-screen controls automatically: left stick to move
(push all the way to sprint), drag anywhere on the right to look, hold to break, tap to
place/use, plus jump, sneak, inventory, pause and chat buttons. Tap hotbar slots to select them.

### Commands

`/gamemode survival|creative`, `/time set day|noon|night|midnight|<n>`, `/weather clear|rain`,
`/tp x y z` (supports `~`), `/give <item> [count]`, `/summon pig|cow|sheep|chicken|zombie|tnt`,
`/kill`, `/seed`, `/spawnpoint`, `/clear`, `/locate <biome>`, `/setblock x y z <block>`,
`/difficulty`, `/keepinventory`, `/help`.

## Features

- **Infinite terrain** generated in Web Workers: 1.18+-style continents, mountains with snowy
  peaks, rivers, oceans and 24 biomes (plains, forests, birch forests, taiga, snowy plains,
  deserts, badlands, savanna, swamps, meadows, cherry groves, jagged peaks, ...).
- **Caves and ores**: cheese and spaghetti caves, lava lakes, a deepslate layer, and coal, copper, iron,
  gold, redstone, lapis, diamond and emerald ores, plus granite/diorite/andesite/tuff.
- **Lighting**: flood-fill sky light and block light (torches, glowstone, lava, furnaces),
  smooth lighting with ambient occlusion, a day/night cycle with sunrise and sunset,
  stars, a moon, 3D clouds and fog.
- **Animated water and lava** with flowing-fluid simulation, plus rain and snow weather.
- **Survival**: health, hunger, saturation, air, fall damage, drowning, XP, mining speeds
  and tool tiers (wood, stone, iron, gold, diamond) with durability.
- **Crafting**: 2×2 and 3×3 crafting, furnace smelting with fuels, chests.
- **Farming**: hoes, farmland that hydrates near water, wheat that grows in stages, bread.
- **Building**: 120+ blocks including slabs (top/bottom, stack into full blocks), ladders,
  torches, glass, wool, ores and metal blocks; half-block step-up like the original.
- **Beds** let you sleep through the night and set your respawn point.
- **Mobs**: pigs, cows, sheep, chickens, undead that burn in daylight, and wall-climbing spiders,
  all with drops; TNT explosions; falling sand and gravel; leaf decay; growing saplings, sugar
  cane and cactus.
- **Creative mode** with flight and a searchable item menu.
- First-person hand, held items, third-person view, block-breaking cracks, particles, synthesized
  sound effects and generative ambient music.
