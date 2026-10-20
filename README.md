# Blockcraft — a Minecraft-style voxel sandbox in one HTML file

**Download [`minecraft.html`](minecraft.html) and open it in a browser. That's it.**
No install, no server, no build step: the whole game is a single self-contained file
(WebGL2 + JavaScript). It works offline once downloaded.

> Fan-made recreation inspired by Minecraft Java Edition 1.21. Not affiliated with
> Mojang or Microsoft. All textures, models, sounds and music are generated
> procedurally in code at startup, so the file contains no copyrighted game assets.
> The Nether and End creatures and the final boss are original designs.

## How to play

1. Download `minecraft.html` (on GitHub: open the file, then click **Download raw file**).
2. Double-click it to open it in Chrome, Edge, Firefox or Safari (any browser with WebGL2).
3. Click **Singleplayer** to create or load a world, or **Quick Play** for a random world.
4. Click inside the game to capture the mouse.

Worlds are saved automatically in your browser (IndexedDB), including the Nether and the End.

### Controls

| Key | Action |
| --- | --- |
| W A S D | Move |
| Space | Jump / swim up (double-tap: toggle flight in creative) |
| Shift | Sneak / fly down |
| Ctrl or double-tap W | Sprint |
| Left click (hold) | Break block / attack |
| Right click | Place block / use / eat / open doors (hold to draw a bow) |
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
`/tp x y z` (supports `~`), `/give <item> [count]`, `/summon <mob>` (pig, cow, sheep, chicken,
zombie, spider, wisp, charred_ghoul, wraith, sentinel, crystal, tnt), `/kill`, `/seed`,
`/spawnpoint`, `/clear`, `/locate <biome|fortress|portal_room>`, `/setblock x y z <block>`,
`/difficulty`, `/keepinventory`, `/dim overworld|nether|end`, `/help`.

## Reaching the End

1. **Build a nether portal**: an obsidian frame (4 wide, 5 tall, corners optional; up to 21×21).
   Obsidian forms where water meets still lava and needs a diamond pickaxe. Light the inside
   with **flint and steel** and stand in the portal for a few seconds.
2. **Explore the Nether**: crimson and warped forests with huge fungi, soul sand valleys,
   basalt deltas, a lava sea, glowstone, quartz, nether gold and ancient debris (smelt it into
   netherite scrap for netherite tools). Nether brick **fortresses** span the lava.
   Floating **Ember Wisps** shoot fireballs and drop *ember dust*; Charred Ghouls roam the caverns.
3. **Collect void pearls** from **Void Wraiths**, tall shadows that teleport around at night in
   the Overworld (and everywhere in the End). Craft **Eyes of the Void** from a void pearl and
   ember dust.
4. **Throw eyes** (right-click) — they fly towards the nearest underground **portal room**.
   Place an eye in each of the 12 end portal frames to open the portal.
5. **The End**: a floating island of end stone ringed by obsidian pillars. **Void Crystals** on the
   pillars keep healing the **Void Sentinel**. Shoot them with a **bow** (or snowballs), then bring
   the Sentinel down — it rests above the central fountain between attacks. Defeating it opens the
   exit portal home and leaves a trophy behind. Thrown void pearls teleport you, too.

## Features

- **Three dimensions** with seamless portal travel and linked portals (8:1 Nether scale):
  the Overworld, the Nether (dense fog, lava sea, ambient spores and ash) and the End
  (starry void sky, outer islands with void reeds).
- **Infinite terrain** generated in Web Workers: 1.18+-style continents, mountains with snowy
  peaks, rivers, oceans and 24 biomes (plains, forests, birch forests, taiga, snowy plains,
  deserts, badlands, savanna, swamps, meadows, cherry groves, jagged peaks, ...), plus five
  Nether biomes.
- **Caves and ores**: cheese and spaghetti caves, lava lakes, a deepslate layer, amethyst geodes,
  cobwebs, and coal, copper, iron, gold, redstone, lapis, diamond and emerald ores.
- **220+ blocks**, including stairs, fences, doors, glass panes, iron bars, lanterns (standing and
  hanging), 16 concrete colours, copper that oxidises over time (scrape it back with an axe),
  polished stones, deepslate tiles, podzol, melons, mushrooms, jack o'lanterns, hay, bone blocks,
  netherrack, nether bricks, blackstone, basalt, soul sand (slows you down), magma (burns),
  crimson/warped wood, shroomlights, crying obsidian, quartz, netherite, end stone, purpur and more.
- **Lighting**: flood-fill sky light and block light, smooth lighting with ambient occlusion,
  a day/night cycle with sunrise and sunset, stars, a moon, 3D clouds and fog.
- **Animated water and lava** with flowing-fluid simulation (lava flows faster in the Nether,
  water boils away there), plus rain and snow weather.
- **Survival**: health, hunger, saturation, air, fall damage, drowning, XP, mining speeds
  and tool tiers (wood, stone, iron, gold, diamond, netherite) with durability.
- **Combat**: swords, critical hits, bows and arrows (charge for more power), snowballs.
- **Crafting**: 2×2 and 3×3 crafting, furnace smelting with fuels, chests.
- **Farming**: hoes, farmland that hydrates near water, wheat that grows in stages, bread.
- **Beds** let you sleep through the night and set your respawn point (they explode outside
  the Overworld).
- **Mobs**: pigs, cows, sheep, chickens, undead that burn in daylight, wall-climbing spiders,
  Ember Wisps, Charred Ghouls, Void Wraiths and the Void Sentinel boss with a boss bar;
  TNT explosions; falling sand and gravel; leaf decay; growing saplings, sugar cane and cactus.
- **Creative mode** with flight and a searchable item menu.
- First-person hand, held items, third-person view, block-breaking cracks, particles, synthesized
  sound effects and generative ambient music with a different mood in each dimension.
