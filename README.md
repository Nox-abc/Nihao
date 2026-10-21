# Blockcraft — a Minecraft-style voxel sandbox in one HTML file

**Download [`minecraft.html`](minecraft.html) and open it in a browser. That's it.**
No install, no server, no build step: the whole game is a single self-contained file
(WebGL2 + JavaScript, under 2 MB). It works offline once downloaded.

> **Blockcraft is NOT AN OFFICIAL MINECRAFT PRODUCT. It is NOT APPROVED BY OR ASSOCIATED WITH
> MOJANG OR MICROSOFT.** It is a fan-made game inspired by Minecraft Java Edition 1.21 (Tricky
> Trials), made for fun. "Minecraft" is a trademark of Mojang Synergies AB.
> All textures, models, sounds and music are generated procedurally in code at startup, so the
> file contains no copyrighted game assets. Paintings are original pictures and music discs play
> original generated tunes. For the official look, load the textures from your own copy of
> Minecraft (see [Resource packs](#resource-packs-and-the-official-minecraft-textures)).

## How to play

1. Download `minecraft.html` (on GitHub: open the file, then click **Download raw file**).
2. Double-click it to open it in Chrome, Edge, Firefox or Safari (any browser with WebGL2).
3. Click **Singleplayer** to create or load a world, or **Quick Play** for a random world.
4. Click inside the game to capture the mouse.

Worlds are saved automatically in your browser (IndexedDB), including the Nether and the End.
Worlds from older versions of Blockcraft are converted when you load them.

### Controls

| Key | Action |
| --- | --- |
| W A S D | Move (and steer boats, minecarts and horses) |
| Space | Jump / swim up (double-tap: toggle flight in creative) |
| Shift | Sneak / fly down / get out of a boat, minecart or saddle |
| Ctrl or double-tap W | Sprint |
| Left click (hold) | Break block / attack |
| Right click | Place / use / eat / open / trade / ride (hold to draw a bow, load a crossbow or raise a shield) |
| Middle click | Pick block |
| 1–9 / mouse wheel | Select hotbar slot |
| F | Swap the items in your main hand and offhand |
| E | Inventory (creative menu in creative mode) |
| Q / Ctrl+Q | Drop item / drop stack |
| T or / | Chat and commands (Tab completes command names and arguments) |
| F1 / F2 / F3 / F5 | Hide HUD / screenshot / debug screen / camera perspective |
| Esc | Pause menu |

In inventories: shift-click moves a stack across, right-click takes half a stack or places one
item, dragging spreads a stack over several slots, double-click gathers matching items, 1–9 swap
with the hotbar, F swaps with the offhand and Q drops.

**Every control can be changed**: open **Options... → Controls...** and click a binding, then press
the new key or mouse button (Esc clears it). Clashing bindings turn red; **Reset Keys** puts all of
them back. The bindings are saved in your browser.

**Night Vision** (in **Options...**) lets you always see, in caves and at night, as if you had
drunk a potion of Night Vision.

**Touch screens** (phones/tablets) get on-screen controls automatically: left stick to move
(push all the way to sprint), drag anywhere on the right to look, hold to break, tap to
place/use, plus jump, sneak, inventory, pause and chat buttons. Tap hotbar slots to select them.

### Commands

| Command | What it does |
| --- | --- |
| `/gamemode survival\|creative` | Switch game mode |
| `/time set day\|noon\|night\|midnight\|<n>`, `/time add <n>` | Change the time |
| `/weather clear\|rain\|thunder` | Change the weather |
| `/tp <x> <y> <z>` | Teleport (`~` means relative) |
| `/give <item> [count]` | Give yourself items, by their Java Edition names |
| `/summon <mob> [x y z]` | Spawn any mob, the Ender Dragon or an end crystal |
| `/kill`, `/kill @e[type=<mob>]` | Kill yourself, or every entity (of one type) |
| `/effect give <effect> [seconds\|infinite] [amplifier]`, `/effect clear [effect]` | Status effects |
| `/enchant <enchantment> [level]` | Enchant the item in your hand |
| `/xp add\|set <amount> [points\|levels]`, `/xp query` | Experience |
| `/gamerule <rule> [true\|false]` | `keepInventory`, `doDaylightCycle`, `doWeatherCycle`, `doMobSpawning`, `commandBlockOutput` (saved with the world) |
| `/locate <structure\|biome>` | Find the nearest structure or biome (vanilla ids such as `monument` or `village_plains` work) |
| `/setblock <x> <y> <z> <block>`, `/fill <x1> <y1> <z1> <x2> <y2> <z2> <block> [replace\|keep\|hollow\|outline\|destroy]` | Edit blocks |
| `/say <message>` | Say something in chat |
| `/spawnpoint`, `/clear`, `/seed`, `/difficulty <0-3>`, `/dim overworld\|nether\|end`, `/help` | Everything else |

Target selectors such as `@p` and `@s` are accepted where the player is meant. Commands also run
from command blocks (see [Redstone](#redstone-and-automation)).

## What's in the game

### The world

- **All 64 biomes of 1.21.** 53 in the Overworld: plains, sunflower plains, forests, flower and
  birch forests, dark forest, jungles, taigas and old-growth taigas, swamps and mangrove swamps,
  deserts, three kinds of badlands, savannas, meadows, cherry groves, groves, snowy plains, ice
  spikes, snowy slopes, jagged, frozen and stony peaks, windswept hills, mushroom fields, beaches,
  rivers and nine kinds of ocean, plus lush caves, dripstone caves and the deep dark underground.
  The Nether has its five biomes and the End its islands.
- **Terrain** generated in Web Workers: continents, mountains, rivers, cheese and spaghetti caves,
  lava lakes, the deepslate layer, amethyst geodes and ores at their vanilla heights, every tree
  type (including mega jungle and spruce trees, mangroves, azaleas and cherry trees), huge
  mushrooms, coral reefs, kelp forests, bamboo, vines, flowers, sweet berries and bee nests.
- **Structures**: villages in five styles with villagers, an iron golem, cats and loot; ancient
  cities in the deep dark; desert pyramids and wells, jungle temples, swamp huts, igloos, pillager
  outposts, ocean monuments, trail ruins, ruined portals, shipwrecks, buried treasure, dungeons,
  mineshafts, trial chambers and strongholds; Nether fortresses and bastion remnants; End cities
  and End ships. Chests are filled from vanilla-style loot tables.
- **Sky and weather**: a day/night cycle with sunrise and sunset, moon phases, stars, 3D clouds,
  fog, rain, snow and thunderstorms with lightning.

### Blocks, items and the inventory

- **Every block and item of Java Edition 1.21**: about 930 blocks and 1,300 items with their real
  names, including the operator blocks (command blocks, structure blocks, jigsaws, barriers, light
  blocks, structure voids). Blocks have their vanilla shapes: stairs, slabs, walls, fences and
  gates, doors, trapdoors, panes, signs, banners, beds, candles, rails, chains, lanterns,
  anvils, chests and more, and plants underwater keep their water.
- **The vanilla creative inventory**: Building Blocks, Colored Blocks, Natural Blocks, Functional
  Blocks, Redstone Blocks, Tools & Utilities, Combat, Food & Drinks, Ingredients and Spawn Eggs
  tabs in the vanilla order, with search, the scroll bar and the survival inventory tab.
- **Survival inventory** with armor and offhand slots, tooltips, rarity colours and the
  enchantment glint.
- **Crafting and workstations**: over 800 recipes in the 2×2 and 3×3 grids; furnace, smoker,
  blast furnace and campfire cooking; stonecutter; smithing table with netherite upgrades and
  armor trims; loom with banner patterns; cartography table; grindstone; anvil; brewing stand;
  enchanting table; and the crafter.

### Survival and combat

- Health, hunger, saturation, experience, fall damage, drowning, freezing in powder snow, and
  mining speeds by tool tier from wood to netherite, with durability.
- Food and exhaustion follow Java Edition: every food restores its vanilla hunger and saturation
  (a steak gives 8 hunger and 12.8 saturation), and sprinting, jumping, swimming, mining,
  fighting and healing tire you at the vanilla rates. Mobs have their Java Edition health, armor,
  attack damage and drops, and difficulty changes them the vanilla way.
- Armor with vanilla protection and toughness, shields, totems of undying, the 1.9 attack
  cooldown, critical hits and sweeping; bows, crossbows, tridents (Loyalty, Riptide, Channeling),
  the mace and its smash attack, wind charges, and elytra with firework boosts.
- 39 status effects, potions (drinkable, splash and lingering), tipped arrows and brewing.
- **Enchanting**: all 42 enchantments, including 1.21's Density, Breach and Wind Burst, from the
  enchanting table (with bookshelves), anvils, enchanted books and villager trades; the
  grindstone takes them off again.

### Mobs

- **80 mobs** built from the vanilla model shapes with procedural skins, in all their variants
  (cats, horses, rabbits, parrots, frogs, axolotls, wolves and more), with babies, armor and held
  items. They path-find, breed, follow food, can be tamed and ridden, and use their vanilla
  attacks: creepers explode (charged ones bigger), skeletons and pillagers shoot, endermen
  teleport and carry blocks, witches throw potions, evokers summon vexes, piglins barter for gold.
- **Villagers** claim job sites and beds, follow a daily schedule, level up and trade in the
  vanilla merchant screen. Zombie villagers can be cured; wandering traders visit with their
  llamas; iron and snow golems defend.
- **The Warden** rises in the deep dark when sculk shriekers are triggered too often: it sniffs,
  roars, punches and fires sonic booms.
- **Ocean monuments** hold guardians and elder guardians, whose curse gives Mining Fatigue III.
- **Bosses**: the Ender Dragon with its end crystals, and the Wither.

### Redstone and automation

- Redstone dust with vanilla signal strength, torches, levers, buttons, pressure plates,
  repeaters, comparators (compare and subtract, and they read containers), observers, targets,
  daylight detectors, sculk sensors and lightning rods.
- Lamps, doors, trapdoors, fence gates, TNT, pistons and sticky pistons, dispensers and droppers,
  hoppers, note blocks, bells, copper bulbs and the crafter all respond.
- **Command blocks**: impulse, chain and repeating, conditional or not, needing redstone or always
  active. Type any of the commands above into the command block screen; `~` coordinates count
  from the block, chains run in the same tick and comparators read whether the command worked.

### Getting around

- Boats, chest boats and bamboo rafts of every wood; minecarts (with chests, hoppers, furnaces or
  TNT) on rails, powered rails, detector rails and activator rails; horses, donkeys, mules,
  camels, pigs and striders to ride.
- Nether portals linked at the vanilla 8:1 scale, and the End portal in strongholds.

### Things to make and use

- Fishing with lure, luck and treasure; maps that draw the world in the vanilla map colours and
  can be zoomed, copied and locked; compasses, recovery compasses, lodestones and clocks.
- Item frames and glow item frames (they show maps), paintings, armor stands, signs you can write
  on (both sides, dye and glow ink, wax), books and quills, lecterns, banners with up to six
  pattern layers, beacons with their pyramid, beam and powers, conduits, jukeboxes and discs.
- Archaeology: brush suspicious sand and gravel in desert pyramids, wells and trail ruins for
  pottery sherds and other finds; brush armadillos for scutes.
- Sponges soak up water and dry out in the Nether.

### Graphics and sound

- Flood-fill sky and block light, smooth lighting with ambient occlusion, animated water and
  lava with flowing fluids, particles, block-breaking cracks, a first-person hand and held items
  that move like vanilla (equipping, swinging, walking bob and sway), a third-person view, a 3D player
  preview in the inventory that follows the mouse, and the vanilla HUD (hearts, hunger, armor, air, experience, effects,
  boss bars).
- Synthesized sound effects for blocks, mobs and items, and generative ambient music with a
  different mood in each dimension.

## Reaching the End

1. **Build a nether portal**: an obsidian frame (4 wide, 5 tall, corners optional; up to 21×21).
   Obsidian forms where water meets still lava and needs a diamond pickaxe. Light the inside
   with **flint and steel** and stand in the portal for a few seconds.
2. **Find a Nether fortress** and kill **blazes** for blaze rods. Grind them into blaze powder.
   Bastion remnants, guarded by piglins and piglin brutes, hold gold and netherite upgrade
   templates.
3. **Collect ender pearls** from endermen, or trade for them with a cleric villager or by
   bartering with piglins. Craft **eyes of ender** from an ender pearl and blaze powder.
4. **Throw eyes of ender** (right-click): they fly towards the nearest **stronghold**. Dig down
   to its portal room and place an eye in each of the 12 end portal frames to open the portal.
5. **The End**: the Ender Dragon circles the island, healed by **end crystals** on top of the
   obsidian pillars. Shoot the crystals with arrows, then bring the dragon down. Its death opens
   the exit portal home, leaves the dragon egg and opens an **End gateway**: throw an ender pearl
   into it to reach the outer islands, with End cities, shulkers, elytra and chorus fruit.
   Four end crystals placed on the exit portal's rim bring the dragon back for another fight
   (each kill opens another gateway).

## Resource packs and the official Minecraft textures

Blockcraft reads Java Edition resource packs, including the textures inside your own copy of
Minecraft, so the game can look like the real thing.

1. Open **Options... → Resource Packs...** (from the title screen or the pause menu).
2. Click **Add Pack File...** (or drag the file onto the list) and pick one of these:
   - **The official Minecraft textures**: the version `.jar` from your Minecraft installation.
     Run that version once in the Minecraft Launcher so the file exists.

     | System | File |
     | --- | --- |
     | Windows | `%APPDATA%\.minecraft\versions\1.21.4\1.21.4.jar` |
     | macOS | `~/Library/Application Support/minecraft/versions/1.21.4/1.21.4.jar` (press Cmd+Shift+G in the file picker to type the path) |
     | Linux | `~/.minecraft/versions/1.21.4/1.21.4.jar` |

     Any version from 1.13 onwards works; newer versions cover more blocks. The pack shows up as
     "Minecraft 1.21.4".
   - **Any resource pack** `.zip`, such as Faithful or packs from Modrinth and CurseForge.
     HD packs up to 128×128 are used at full resolution; bigger ones are scaled down to 128×128.
3. Click **Done**. The game switches over straight away, even in the middle of a world.

You can stack several packs. The pack at the top of the list wins, and anything it does not
include comes from the next pack down, then from Blockcraft's own art. Use ▲ ▼ to reorder packs,
**Use** / **Turn off** to switch one on or off, and **Default Textures** to go back to the built-in
look. Packs are saved in your browser, so you only add them once. The file is read on your
computer and is never uploaded anywhere, and none of Mojang's assets are included in this repository.

What a pack changes:

- **Blocks and items**, including animated textures (`.mcmeta`), grass, foliage and water tinting,
  block-breaking cracks, chests, beds, signs, banners, the end portal, compass and clock frames,
  and paintings.
- **Mobs**: every mob uses the vanilla model shapes and texture layout, so the pack's entity
  textures fit directly, and the player uses the pack's Steve skin.
- **Interface**: the hotbar, hearts, hunger, armor, air and experience bar, crosshair, buttons,
  the title logo, the menu background, the font, the creative inventory tabs, and the windows of
  the inventory, crafting table, furnaces, chests, brewing stand, enchanting table, anvil,
  villagers and the other workstations.
- **Sky and effects**: sun, moon phases, clouds, the End sky, rain, snow and particles.

### A personal copy with your packs built in

**Save Game With These Packs...** on the Resource Packs screen downloads a copy of the game with the
packs that are switched on built in, and switched on from the first start, for example a
`minecraft-Minecraft_1.21.4.html` that looks like the real game wherever you open it. The copy is
made on your computer from the files you added. A copy built from your own Minecraft `.jar`
contains Mojang's textures, so keep it for yourself and don't share or upload it; the repository's
`.gitignore` leaves such copies out so they can't be committed by accident.
