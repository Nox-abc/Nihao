# Blockcraft — a Minecraft-style voxel sandbox in one HTML file

**Download [`minecraft.html`](minecraft.html) and open it in a browser. That's it.**
No install, no server, no build step: the whole game is a single self-contained file
(WebGL2 + JavaScript, about 2 MB). It works offline once downloaded.

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
3. Click **Singleplayer** to create or load a world, or **Quick Play** for a random world. A new
   world can be Survival, Hardcore or Creative, with its own difficulty and **Allow Commands**
   (see [Game modes](#game-modes)).
4. Click inside the game to capture the mouse.

Worlds are saved automatically in your browser (IndexedDB), including the Nether and the End.
Worlds from older versions of Blockcraft are converted when you load them (they keep their own
terrain style; new worlds get Java Edition's terrain, see [Terrain](#java-edition-terrain-from-java-seeds)).
The **Select World** screen works like Java Edition's: a search box, each world with its icon (a
picture of the world taken a few seconds into your first visit), **Edit** (rename it, reset its
icon, make a backup copy), **Delete** (after asking), and **Re-Create** (a new world with the same
seed, type and settings). Loading a world shows its progress and a map of the chunks being made,
and a portal trip shows "Loading terrain..." over the portal. The first time you play, Survival
shows Java's first-time hints one after another: move and look around, find a tree, break it, open
your inventory and craft planks.

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
| 1–9 / mouse wheel | Select hotbar slot (the wheel sets the flying speed in spectator mode) |
| F | Swap the items in your main hand and offhand |
| E | Inventory (creative menu in creative mode) |
| Q / Ctrl+Q | Drop item / drop stack |
| T or / | Chat and commands (Tab completes command names and arguments) |
| F1 / F2 / F3 / F5 | Hide HUD / screenshot / debug screen / camera perspective |
| F3+N / F3+F4 | Switch to spectator mode and back / the game mode switcher (hold F3, press F4 to pick, let go of F3); both need Allow Commands |
| F3+B / F3+G / F3+H | Hitboxes / chunk borders / advanced tooltips (item ids and durability) |
| F3+C / F3+I / F3+D / F3+A / F3+T / F3+Q | Copy your location as a /tp command / copy the block you look at / clear the chat / reload chunks / reload resource packs / list these |
| L | Advancements |
| C+1–9 / X+1–9 | Save / load a whole hotbar (creative mode; the saved ones are also in the Saved Hotbars tab) |
| Tab (hold) | Player list (shows a scoreboard objective set to the `list` slot) |
| Ctrl+B | Narrator on/off |
| Esc | Pause menu |

In inventories: shift-click moves a stack across, right-click takes half a stack or places one
item, dragging spreads a stack over several slots, double-click gathers matching items, 1–9 swap
with the hotbar, F swaps with the offhand and Q drops.

**Every control can be changed**: open **Options... → Controls... → Key Binds...** and click a
binding, then press the new key or mouse button (Esc clears it). Clashing bindings turn red;
**Reset Keys** puts all of them back. The bindings are saved in your browser.

**Night Vision** (in **Options... → Video Settings**) lets you always see, in caves and at night,
as if you had drunk a potion of Night Vision.

### Options

The Options screen is laid out like Java Edition 1.21's: FOV and the world's difficulty (with the
lock that keeps it for good) on top, then **Skin Customization**, **Music & Sounds**, **Video
Settings**, **Controls**, **Language**, **Chat Settings**, **Resource Packs**, **Accessibility
Settings**, **Telemetry Data** and **Credits & Attribution**. Menus blur the world behind them, and
the settings do what they do in Java:

- **Video**: Graphics Fast / Fancy / Fabulous! (Fast draws leaves as solid blocks with dark gaps, as
  Java does; rain distance, the dark screen edges in dark places; Fabulous! also shows particles and
  rain behind water and glass), render and simulation
  distance (mobs move and crops grow only that far), Chunk Builder, Max Framerate, GUI Scale (Auto
  and 1 up to what the window allows), the Attack Indicator under the crosshair or beside the
  hotbar, Clouds Off / Fast / Fancy, Particles All / Decreased / Minimal, Mipmap Levels (the smaller
  texture copies are made the way Java makes them, so far-away leaves get fuller and darker instead of
  thinning out, and plants, glass, doors, rails and torches always use the full-size texture), round
  **entity shadows**, Distortion and FOV Effects, Entity Distance, the autosave note, enchantment
  Glint Speed and Strength, Menu Background Blur and Biome Blend.
- **Music & Sounds**: a volume for each category (music, jukeboxes and note blocks, weather,
  blocks, hostile and friendly creatures, players, ambient), **subtitles** with arrows showing where
  a sound comes from, and Directional Audio (3D sound for headphones).
- **Controls**: mouse sensitivity, Invert Mouse, scroll sensitivity and discrete scrolling, raw
  input, Sneak and Sprint as Hold or Toggle, **Auto-Jump**, the **Operator Utilities** creative tab
  (command blocks, structure blocks, barriers, light...) and the key binds.
- **Chat**: Shown / Commands Only / Hidden, colours, clickable web links, text opacity, background
  opacity, size, line spacing, delay, width and heights, command suggestions while you type, and the
  **narrator** (your browser reads the chat aloud).
- **Accessibility**: High Contrast buttons, text backgrounds everywhere, notification time, Darkness
  Pulsing, Damage Tilt, hiding lightning flashes and splash texts, panorama speed.
- **Skin Customization**: the jacket, sleeves, pants legs and hat layers of your skin, and **Main
  Hand** Right or Left (the hands, the off-hand slot and the attack indicator swap sides).

### Performance

- Chunk sections hidden behind solid ground are not drawn, as with Java's cave culling: the game
  walks from your position through the openings of each 16x16x16 section, so caves you can't see
  into and the rock under your feet cost nothing to draw.
- Mobs, items and other entities are drawn only as far as Java draws them (64 blocks for each
  block of their size, further with a bigger render distance or **Entity Distance**), and only
  the ones within the **Simulation Distance** move.
- On a slow computer: lower **Render Distance** and **Render Resolution**, set **Graphics** to
  Fast, **Particles** to Minimal and **Clouds** off, or cap **Max Framerate**.

**Touch screens** (phones/tablets) get on-screen controls automatically: left stick to move
(push all the way to sprint), drag anywhere on the right to look, hold to break, tap to
place/use, plus jump, sneak, inventory, pause and chat buttons. Tap hotbar slots to select them.

### Commands

Commands work like Java Edition 1.21's, with its syntax and its feedback:

- **Target selectors** `@p`, `@r`, `@a`, `@e`, `@s` and `@n` with their arguments (`type`, `tag`,
  `name`, `distance`, `x`/`y`/`z`/`dx`/`dy`/`dz`, `limit`, `sort`, `scores`, `level`, `gamemode`,
  `x_rotation`, `y_rotation`, `advancements`, `nbt`), negation (`type=!zombie`) and entity tags
  (`#skeletons`, `#raiders`...).
- **Coordinates**: absolute, relative `~` and local `^ ^ ^` (left, up, forward); rotations.
- **`/execute`** with `as`, `at`, `positioned` (also `as` and `over`), `rotated`, `facing`,
  `anchored`, `align`, `in`, `on`, `summon`, `if`/`unless` (`block`, `blocks`, `entity`, `score`,
  `biome`, `dimension`, `loaded`, `items`, `data`), `store result|success` (scores, boss bars,
  entity health and motion) and `run`.
- **Scoreboards**: objectives with `dummy`, `trigger`, `deathCount`, `totalKillCount`, `health`,
  `food`, `air`, `armor`, `level`, `xp` and every statistic (`minecraft.mined:minecraft.stone`,
  `minecraft.custom:minecraft.jump`...), the sidebar, `/scoreboard players` with `operation`,
  `/trigger`, and teams.
- **Text**: `/tellraw` and `/title` (title, subtitle, action bar, times) with JSON text (colours,
  bold, italic, `selector` and `score` parts), `/say`, `/me`, `/msg`, `/teammsg`.
- **The world border** (`/worldborder` set, add over time, center, damage, warning) with its striped
  wall, its push-back and its damage.
- And: `/tp` (to entities, with rotation or `facing`), `/kill`, `/give` (with 1.21 item components
  like `diamond_sword[enchantments={levels:{sharpness:5}}]`), `/clear`, `/effect`, `/enchant`,
  `/xp`, `/summon` (with NBT such as `{NoAI:1b,Tags:["a"],CustomName:'"Bob"'}`), `/setblock`,
  `/fill` (with `replace <filter>`), `/clone` (`masked`, `filtered`, `move`, `force`),
  `/fillbiome`, `/data get|merge`, `/item replace`, `/loot`, `/particle`, `/playsound`,
  `/stopsound`, `/bossbar`, `/tag`, `/team`, `/spawnpoint`, `/setworldspawn`, `/spreadplayers`,
  `/ride`, `/damage`, `/attribute`, `/random`, `/tick` (rate, freeze, step, sprint), `/forceload`,
  `/spectate`, `/difficulty`, `/list`, `/time`, `/weather`, `/gamemode`, `/defaultgamemode`,
  `/gamerule`, `/locate`, `/recipe`, `/advancement`, `/seed` and `/help`.

Command blocks (impulse, chain, repeating, conditional) run them from their own position, so
selectors and `~` count from the block (see [Redstone](#redstone-and-automation)). There are no
data packs, so `/function` and `/schedule` have nothing to run.

Commands need **Allow Commands**, set when the world is created like in Java Edition: off for
Survival, on for Creative, always off for Hardcore (Quick Play worlds and worlds from earlier
versions of Blockcraft have it on). Without it, only the commands any Java player has are there
(`/help`, `/seed`, `/me`, `/msg`, `/list`, `/random`, `/trigger`, `/teammsg`).

## What's in the game

### The world

- **All 67 biomes of Java Edition 26.3.** 56 in the Overworld: plains, sunflower plains, forests, flower and
  birch forests, dark forest, pale gardens, dappled forests, jungles, taigas and old-growth taigas, swamps and
  mangrove swamps, deserts, three kinds of badlands, savannas, meadows, cherry groves, groves, snowy plains, ice
  spikes, snowy slopes, jagged, frozen and stony peaks, windswept hills, mushroom fields, beaches,
  rivers and nine kinds of ocean, plus lush caves, dripstone caves, sulfur caves and the deep dark underground.
  The Nether has its five biomes and the End its islands.
- **Java Edition terrain**: new worlds are built by a port of Java Edition 26.3's own world
  generator, so a seed gives the same mountains, rivers, caves and biomes as in Minecraft (see
  below). Worlds run from y −64 to 319, with the deepslate layer, aquifers, copper and iron ore
  veins, and lava lakes, amethyst geodes, dungeons and ores at their vanilla heights.
- **Decoration like Java Edition**: the trees (every kind, from fancy oaks and mega jungle trees to
  mangroves, azaleas over rooted dirt, cherry trees, pale oaks hung with moss and hiding creaking hearts,
  and the dappled forests' red, orange and yellow poplars), flowers and eyeblossoms, grass, bushes, dry grass, leaf
  litter, pale moss, ores, lakes, springs, geodes, dungeons, icebergs, ice spikes, coral reefs, kelp forests,
  bamboo, vines, bee nests, glow lichen, moss and dripleaves in lush caves, dripstone, sulfur spikes and potent
  sulfur pools in the sulfur caves, and sculk in the deep dark, each where Java Edition puts it for the seed (see below).
- **Structures**: villages in five styles with villagers, an iron golem, cats and loot (now and then an
  abandoned one, taken over by zombie villagers and cobwebs); ancient
  cities in the deep dark; desert pyramids and wells, jungle temples, swamp huts, igloos, pillager
  outposts, ocean monuments, trail ruins, ruined portals, shipwrecks, buried treasure, dungeons,
  mineshafts, trial chambers and strongholds; Nether fortresses and bastion remnants; End cities
  and End ships. Chests are filled from vanilla-style loot tables.
- **Sky and weather**: a day/night cycle with sunrise and sunset, moon phases, stars, 3D clouds,
  fog, rain, snow and thunderstorms with lightning.

### Java Edition terrain from Java seeds

Type a seed on the **Create New World** screen exactly as you would in Minecraft Java Edition
(a number, or any text, which is turned into a number the way Java does it). Blockcraft runs a
JavaScript port of Java Edition's world generator in background workers (the terrain, the biomes and the
decoration of 26.3):

- **The same terrain**: the noise router (continents, erosion, peaks and valleys, the terrain
  splines), cell interpolation, cheese, spaghetti and noodle caves, aquifers, ore veins, the
  surface rules of every biome, carver caves and canyons, and the 3D biomes, so lush caves,
  dripstone caves and the deep dark sit underground where they do in Java Edition.
- **The same world spawn**, found the vanilla way, and **F3** shows vanilla coordinates and the
  biome with Java's fuzzy biome borders.
- **The same structure positions**: villages (with the same village type), desert pyramids,
  jungle temples, swamp huts, igloos, pillager outposts, ocean monuments, shipwrecks, ruined
  portals, ancient cities, trail ruins, trial chambers, buried treasure, mineshafts, desert wells
  and all 128 strongholds start where Java Edition starts them, so `/locate` and seed maps agree.
  The buildings themselves are Blockcraft's own designs, not Mojang's, but they sit on the land the way Java's
  do: villages and pillager outposts shape the ground around their buildings with Java's own terrain adaptation,
  and abandoned villages turn up where Java's do.

How it was checked: the biomes against [cubiomes](https://github.com/Cubitect/cubiomes) for tens
of thousands of positions on several seeds (Large Biomes too, with 1.21's layout), and since Part 64 26.3's
layout, with its pale gardens, dappled forests and sulfur caves, against Pumpkin's 26.3 biomes on 58 chunks
(89,088 cells of 4×4×4 blocks, all but one the same); the terrain splines, default and
amplified, value for value against Java Edition 1.21's worldgen data; the terrain noise, aquifers, surface and carvers
block-for-block against chunks generated by Java Edition 1.21, and since Part 62 the caves, ore
veins and surface of 26.3 block-for-block against 95 chunks on two seeds from
[Pumpkin](https://github.com/Pumpkin-MC/Pumpkin)'s 26.3 generator (itself tested against Java Edition 26.3),
apart from 6 single blocks at cave edges; the spawn point, the structure
starts and the strongholds against cubiomes.

- **The same trees, plants, ores and caves' decorations** (since Part 63): every chunk is decorated by a
  port of Java Edition's decoration step, with 26.3's features and their settings, each feature in
  Java's order, drawing Java's random numbers for that chunk and that feature. Checked block for
  block against Pumpkin's 26.3 generator on 52 chunks: 35 come out identical, and the others differ
  only where the reference itself leaves out or simplifies a 26.3 feature (sculk patches, dripstone,
  the sulfur caves, and the plants Java removes at the edge of a tree). The new biomes of Part 64 too: a pale
  garden and a dappled forest come out identical once the two things the reference leaves out are left out here
  (the moss patch at the foot of a pale oak, and shelf mushrooms, whose placement Blockcraft has to guess as no
  reference has it), and the sulfur caves' stone bands match the reference except that Blockcraft samples them
  in 3D as 26.3's data asks (the reference flattens them). Where the features of two
  chunks overlap at their border, Java's result depends on which chunk it decorated first; Blockcraft
  gives one of those results, the same however the world is explored. Fossils and desert wells
  (which Java builds from structure files) aren't placed yet, nor the sulfur caves' springs and 26.3's abandoned
  camps (structure files too). Chunks of worlds made before this
  version keep their old decoration, so a tree can be cut off where old and new chunks meet.

### Creating a world

The **Create New World** screen has Java Edition 1.21's three tabs:

- **Game**: the world's name, the game mode (Survival, Hardcore, Creative), the difficulty and
  Allow Commands.
- **World**: the **world type** (click to go through them, shift-click to go back), the seed,
  **Generate Structures** and **Bonus Chest**.
  - **Default**.
  - **Superflat**: layers of blocks from the bottom of the world under one biome. **Customize**
    lists the layers (remove the ones you don't want) and **Presets** has Java's nine: Classic
    Flat, Tunnelers' Dream, Water World, Overworld, Snowy Kingdom, Bottomless Pit, Desert,
    Redstone Ready and The Void, each with its own structures (villages in Classic Flat, ocean
    monuments in Water World...) and, for some, the biome's trees, ores and lakes. The preset
    text works like Java's: copy it to share a world's layers, or paste your own, like
    `minecraft:bedrock,3*minecraft:stone,minecraft:grass_block;minecraft:cherry_grove`.
  - **Large Biomes**: Java's large-biomes noise, every biome four times as wide.
  - **Amplified**: Java's amplified terrain, mountains that reach the build limit (hard on
    slower computers).
  - **Single Biome**: the default terrain, all of it one biome you pick with **Customize**.

  With **Generate Structures** off there are no villages, temples, strongholds, fortresses,
  bastions or end cities (dungeons and desert wells are features and stay), so Eyes of Ender
  find nothing. The **Bonus Chest** (not in hardcore) holds Java's starting loot, with a torch on
  each side, next to the spawn.
- **More**: **Game Rules**, an editor for all 49 game rules by category, for the new world.

### Blocks, items and the inventory

- **Every block and item of Java Edition 1.21, and the blocks of 26.3's new biomes**: about 1,020 blocks and
  1,400 items with their real names, including the operator blocks (command blocks, structure blocks, jigsaws, barriers, light
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
- **The recipe book**: the green book by the crafting grid in the inventory, on the crafting table
  and on the furnace, smoker and blast furnace opens Java Edition's recipe book, with its tabs
  (equipment, building blocks, miscellaneous and redstone; food, blocks and miscellaneous for the
  furnaces), a search box, the craftable filter and pages. Click a recipe to move its ingredients
  into the grid (shift-click for as many as you can make, click again for one more); if something
  is missing, a ghost of the recipe shows what goes where. Recipes unlock the first time you get
  one of their ingredients, with a **New Recipes Unlocked!** toast. `doLimitedCrafting` and
  `/recipe` work like Java's.

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

### Game modes

- **Survival** and **Creative** as you know them.
- **Adventure**: everything Survival has, but blocks can't be broken or placed. Doors, buttons,
  levers, chests, crafting tables, beds, villagers, vaults and other things you use still work,
  and so do food, bows, tridents, snowballs, ender pearls, armor and boats; items that do
  something to a block (buckets, bone meal, hoes, flint and steel, spawn eggs, item frames,
  minecarts) don't, nor do repeaters, comparators, daylight detectors and signs, and armor stands
  can't be knocked down. There is no block outline.
- **Spectator**: fly through everything at the speed the mouse wheel sets (shift goes down).
  Nothing can hurt you but the void, mobs don't see you, arrows and explosions pass you by, you
  pick nothing up and set off no pressure plates or portals. Right-click a chest, furnace,
  crafting table or anything else with a menu to look inside (without taking anything);
  left-click a mob to see through its eyes (a creeper's are green, a spider's blurry, an
  enderman's inverted) and sneak to come back. No hotbar, hearts or hand; the crosshair only
  shows over a mob or something you can open, and inside the ground you see the caves.
- **Hardcore**: Survival locked on Hard with its own hearts and no commands. When you die it is
  **Game Over**, and **Spectate World** brings you back as a spectator.
- Each world keeps its own **difficulty** (the Options setting changes the world you are in;
  on the title screen it is the one new worlds start with). The death screen shows your score
  (the experience collected since your last death).

### Advancements and statistics

- **Advancements**: the 121 advancements of Java Edition 1.21 in its five tabs (the story, the
  Nether, the End, adventure, husbandry), with vanilla's goals, tree, frames (task, goal,
  challenge), hidden ones and experience rewards, described in our own words. Each one pops up as
  a toast and in the chat (`announceAdvancements`); **L** or the pause menu opens the screen with
  the trees, tooltips and progress (5/53 biomes and so on).
- **Statistics** (pause menu): time played, distances walked, sprinted, swum, flown, fallen and
  ridden, jumps, damage dealt and taken, deaths, kills, animals bred, fish caught, trades,
  workstations used and the rest of the General tab; each block mined and item crafted, used,
  broken, picked up and dropped; each mob killed and killed by. Kept in the save.

### Mobs

- **80 mobs** built from the vanilla model shapes with procedural skins, in all their variants
  (cats, horses, rabbits, parrots, frogs, axolotls, wolves and more), with babies, armor and held
  items. They path-find, breed, follow food, can be tamed and ridden, and use their vanilla
  attacks: creepers explode (charged ones bigger), skeletons and pillagers shoot, endermen
  teleport and carry blocks, witches throw potions, evokers summon vexes, piglins barter for gold.
- **Villagers** claim job sites and beds, follow a daily schedule, level up and trade in the
  vanilla merchant screen. Zombie villagers can be cured; wandering traders visit with their
  llamas; iron and snow golems defend.
- **The Warden** rises in the deep dark when sculk shriekers are triggered too often: it follows
  vibrations, sniffs out whoever is near, roars, punches and fires sonic booms through walls.
- **Ocean monuments** hold guardians and elder guardians, whose curse gives Mining Fatigue III.
- **Bosses**: the Ender Dragon with its end crystals, and the Wither.

### Spawning and mob farms

Mobs appear and disappear the way Java Edition's natural spawner does it, so farm designs from
Java tutorials work:

- **Natural spawning** every tick in the chunks within 128 blocks: one spot per chunk between the
  bottom of the world and its top block, packs of up to four, never within 24 blocks of you or
  the world spawn, and the vanilla mob caps (70 monsters, 10 animals every 20 seconds, 15 bats,
  5 squid, 5 glow squid, 5 axolotls, 20 fish).
- **The vanilla rules for every spot**: each biome's 1.21 spawn list and weights, monsters only
  in the dark (block light 0 in the Overworld and the End, 7 or less in the Nether, with the
  vanilla sky-light test), what mobs may stand on (not glass,
  leaves, ice, bedrock, trapdoors, copper grates or bottom slabs; jack o'lanterns are fine), room
  for the whole body, nothing spawning in rails, carpets, buttons or other redstone parts, and
  each mob's own conditions (husks and strays under open sky, drowned in water, slimes in slime
  chunks below y 40 and in swamps by moonlight, guardians under the monument's roof, bats in the
  dark below sea level, more of them around Halloween).
- **Structures** keep their own mobs: witches and cats in swamp huts, guardians in ocean
  monuments, pillagers at outposts, blazes and wither skeletons in fortresses, and nothing
  spawns inside ancient cities or trial chambers.
- **Despawning**: monsters vanish beyond 128 blocks at once, and after 30 seconds of idling now
  and then beyond 32; animals, named and tamed mobs stay. Mobs more than 32 blocks from you stop
  wandering, as in Java Edition.
- **Slime chunks** are Java Edition's for the seed, and a new chunk's first animals are chosen
  and placed with Java Edition's random numbers for that chunk, so a seed starts with the same
  herds, among the same trees and plants as Java Edition's.
- **Spawners** try four times every 10 to 40 seconds within 4 blocks when you are within 16,
  need darkness but no floor, and stop at six mobs around them.
- **The trapdoor trick**: mobs treat trapdoors, lily pads and big dripleaves as somewhere to
  stand, so they walk off spawning floors into drops and water channels. Flowing water pushes
  mobs and items with Java Edition's currents.
- **Iron farms**: villagers that slept in the last day and haven't seen a golem for 30 seconds
  call an iron golem when three of them panic (a zombie nearby) or five gossip. XP and
  player-only drops come only from mobs you hurt in their last 5 seconds.
- Phantoms come after three sleepless days, and wandering traders on vanilla's daily odds.
- **Zombie sieges**: one midnight in ten, twenty zombies come into the village you are in. Cats
  turn up in villages with five claimed beds, and black cats at swamp huts.

### Raids and patrols

- **Pillager patrols** roam from the fifth day: a few pillagers led by a captain carrying the
  Ominous Banner, appearing 24 to 48 blocks away in daylight now and then. Pillager captains
  (also at outposts) drop an ominous bottle; drinking it gives Bad Omen I to V.
- **Raids**: walk into a village with Bad Omen and it turns into Raid Omen; 30 seconds later the
  raid begins. Waves of pillagers, vindicators, evokers, witches and ravagers (with riders in the
  late waves) come from 64 blocks out, 3, 5 or 7 waves by difficulty and a bonus wave for a
  strong omen, each led by a captain. The red raid bar counts down between waves and shows the
  raiders' health, then Victory or Defeat. The raid is lost if the villagers are all gone.
- Winning makes you a **Hero of the Village** for 40 minutes: villagers trade at a discount.
- The `doPatrolSpawning`, `doTraderSpawning`, `doInsomnia` and `disableRaids` game rules work
  like Java Edition's.

### Trial chambers

- **Trial spawners** work like Java Edition 1.21's: each has its mob's vanilla config (zombies,
  husks and spiders; slimes, cave spiders, silverfish and baby zombies; skeletons, strays and
  bogged, some of them slow; breezes), wakes up when it sees you within 14 blocks, sends its wave
  (six mobs, three at a time for most, more for every extra player it saw), then throws out a
  trial key or food and potions for each player and rests for 30 minutes. Its mob turns inside it
  while it waits.
- **Ominous trials**: come near a trial spawner with Bad Omen and it becomes Trial Omen (15
  minutes for each level). Every trial spawner you meet with it turns ominous: blue flames,
  bigger waves of spiders, slimes and other small mobs, zombies and skeletons in copper-trimmed
  armor with three protections and swords or bows, and ominous item spawners that drop lingering
  potions, arrows, fire charges or wind charges onto you and its mobs every 8 seconds. It gives
  ominous trial keys (3 in 10) or better food.
- **Vaults** light up when a player who has not opened them comes within 4 blocks and take one
  key per player: the item they would give turns inside, and the rewards come out one by one.
  Ominous vaults take ominous keys for the ominous rewards (heavy cores, enchanted golden apples,
  Wind Burst books, the Creator disc). All rewards, the chambers' chests and barrels, and the gear
  of ominous mobs use the vanilla loot tables.
- The potions of the ominous trials: **Wind Charged** mobs burst like a wind charge when they die,
  **Weaving** leaves cobwebs (and lets you through them faster), **Oozing** two slimes, and
  **Infested** lets out silverfish when hit.
- A trial spawner placed by hand waits for a spawn egg to give it a mob; a placed vault takes a
  trial key.

### Game rules

All 49 of Java Edition 1.21's game rules can be set with `/gamerule`, and they do what they do in
Java: `keepInventory`, `mobGriefing` (creepers, ghasts and the wither break nothing, endermen
leave blocks alone, sheep eat without leaving dirt, farmers stop harvesting), `doFireTick`,
`randomTickSpeed` (for crop farms), `doTileDrops`, `doMobLoot`, `doEntityDrops`,
`naturalRegeneration`, `fallDamage`, `fireDamage`, `drowningDamage`, `freezeDamage`,
`doImmediateRespawn`, `showDeathMessages`, `sendCommandFeedback`, `commandBlockOutput`,
`commandModificationBlockLimit`, `doDaylightCycle`, `doWeatherCycle`, `doMobSpawning`,
`doPatrolSpawning`, `doTraderSpawning`, `doInsomnia`, `doWardenSpawning`, `doVinesSpread`,
`disableRaids`, `waterSourceConversion`, `lavaSourceConversion`, `snowAccumulationHeight`,
`maxEntityCramming`, `spawnRadius`, `playersSleepingPercentage`, `forgiveDeadPlayers`,
`enderPearlsVanishOnDeath`, `projectilesCanBreakBlocks`, `reducedDebugInfo`, the three explosion
drop decay rules and the rest (the ones about servers are accepted and kept).

### Fire, explosions and weather

- **Fire** spreads like Java Edition's: each fire ages on its own ticks, catches blocks by their
  vanilla ignite and burn odds (leaves and wool fast, planks slower, logs slowly), burns out on
  stone, faster in humid biomes and in the rain, and lava sets nearby wood alight.
- **Explosions** cast vanilla's 1352 rays, stopped by each block's blast resistance: obsidian and
  water hold, TNT under water breaks nothing, TNT next to a blast goes off with a short fuse.
  Creatures take damage by how much of them the blast can see, so walls protect, and Blast
  Protection softens the push. TNT drops every block it breaks; creepers drop one in three.
  Primed TNT drifts with water currents and bounces, so TNT cannons work.
- **Snow and ice**: snow settles in cold biomes while it snows (layer on layer up to
  `snowAccumulationHeight`), cold ponds freeze from their edges, and cauldrons fill with rain or
  powder snow. Packing more than 24 creatures into one spot hurts them (entity cramming).

### Redstone and automation

- Redstone dust with vanilla signal strength, torches, levers, buttons, pressure plates,
  repeaters, comparators (compare and subtract, and they read containers), observers, targets,
  daylight detectors, sculk sensors and lightning rods.
- Lamps, doors, trapdoors, fence gates, TNT, pistons and sticky pistons, dispensers and droppers,
  hoppers, note blocks, bells, copper bulbs and the crafter all respond. Pistons, dispensers and
  droppers have Java Edition's quasi-connectivity: power reaching the block above them counts, but
  they only notice it at the next block update next to them, so block update detectors work.
  Slime blocks carry power like solid blocks; observers and blocks of redstone don't.
- Java Edition timings and quirks: repeaters stretch a short pulse to their delay and lock when a
  powered repeater or comparator points into their side, redstone torches burn out when switched
  off eight times in three seconds, pressure plates stay down for a second (weighted ones half a
  second), and observers see crops grow.
- Hoppers point down or sideways into whatever they were placed against (into a furnace's side
  goes fuel), and pistons break melons, pumpkins, beds, doors, pots and other fragile blocks
  instead of pushing them, so automatic farms built from Java designs work. Pistons push up to 12
  blocks, slime and honey blocks drag the blocks around them, and moved blocks slide for 2 ticks.
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
- **Decorated pots**: craft them from four bricks or pottery sherds and the sherds' pictures show
  on its sides (each of the 23 sherds has its own). A pot holds one stack: put items in by hand
  or with a hopper, take them out with a hopper below, and a comparator reads how full it is. A
  sword, axe, pickaxe, shovel, hoe, trident or mace (without Silk Touch), or an arrow, shatters
  it into its sherds; broken by hand it keeps its sides. Trial chambers have pots with flow,
  guster and scrape sherds, some holding loot.
- Sponges soak up water and dry out in the Nether.
- **Fireworks**: a firework star is gunpowder and dyes, plus a fire charge (large ball), a gold
  nugget (star), a feather (burst) or any head (creeper face), a diamond for a trail and glowstone
  dust for a twinkle; craft a star with more dyes to make it fade to those colours. A rocket is
  paper, one to three gunpowder (how high it flies) and any stars. Used on the ground it climbs and
  bursts into sparks in the stars' shapes and colours, and rockets with stars hurt what is close
  when they go off. Dispensers shoot rockets straight out, crossbows fire them, and a rocket used
  while flying with an elytra pulls you along for as long as it lasts.
- **Chiseled bookshelves**: right click one of the six slots on the front to put a book in or take
  it out (the front shows which slots are full). Hoppers fill and empty them, and a comparator
  reads the last slot used (1 to 6).
- **Goat horns**: eight horns with their own calls (Ponder, Sing, Seek and Feel from ordinary goats
  and outposts; Admire, Call, Yearn and Dream from screaming goats). A horn rests for 7 seconds
  after it plays, shown on the hotbar like the ender pearl's cooldown. A goat that rams into
  stone, logs, packed ice or some ores snaps off one of its horns.
- **The mace**: Breach makes the target's armor work less well, a smash attack knocks back
  everything standing around the target, and Wind Burst throws you back up; landing no lower than
  where you hit costs no health.
- A mob head on top of a note block makes it play that mob's sound.
- **Wolves of every coat**: the nine coats of 1.21 come from the biome a wolf spawns in (pale in
  taigas, ashen in snowy taigas, black and chestnut in the old growth taigas, rusty in jungles,
  snowy in groves, spotted in savannas, striped in badlands, woods in forests); a pack shares one
  coat and a pup takes one of its parents'. Tamed wolves have 40 health, eat meat or fish to heal
  twice what the food is worth, and stand up when they are hurt.
- **Wolf armor**: the owner puts it on a grown tame wolf with a right click and takes it off with
  shears. It takes every hit it can (not falls, fire, lava, magic and the like), losing as much
  durability as the damage, shows cracks as it wears down and breaks when it runs out; armadillo
  scutes mend it while the wolf sits. It always drops when its wolf dies.
- **Dyeing**: leather armor, leather horse armor and wolf armor are dyed in the crafting grid with
  one or more dyes, mixed like Java (dyeing again mixes with the old colour). Dyed items say so in
  their tooltip, and a water cauldron washes the dye off.
- **Wind charges** burst like Java's: a charge thrown from your eyes flies straight until it hits
  something (they rest half a second between throws, and dispensers shoot them too). The burst
  throws everything near it away by how close it is and how much of it the blast sees, so
  throwing one at your feet sends you about 6 blocks up, and falling no lower than where it hit
  you costs no health. It opens and closes wooden and copper doors, trapdoors and gates, presses
  buttons, flips levers, rings bells and puts out candles. A breeze's charge bursts bigger, and only
  works blocks with mobGriefing on. Hit a charge to send it back where you look. A mace with Wind
  Burst now makes the same kind of burst at your feet.
- **Bells** ring when used from the side they swing to, when a projectile hits that side, by
  redstone and by wind. Villagers near a ringing bell run to their beds, and raiders near one glow
  for a few seconds.
- An axe (in a vindicator's or a piglin brute's hand, say) or the warden hitting your raised
  shield knocks it out for 5 seconds.
- **Horse inventories**: sneak and right click a tamed horse, donkey, mule, llama or skeleton
  horse, or any camel (or press the inventory key while riding it), for its screen like Java's:
  the saddle, the armor (or a llama's carpet), the chest and the animal itself turning to follow
  the mouse.
- **Horse armor** goes on a tamed horse with a right click or in its screen and protects it like
  Java's (3, 5, 7 or 11 armor); it is drawn on the horse, leather horse armor in its dye.
  **Carpets** on llamas show as blankets in their colour.
- **Chests** on donkeys and mules hold 15 stacks, on llamas 3 a point of strength (strength is 1
  to 3, now and then up to 5, and a young llama takes after its stronger parent). Everything an
  animal carries drops when it dies.
- **Riding**: hold jump to fill the jump bar (it takes the experience bar's place) and let go to
  jump, higher the fuller it is; the mount's hearts take the food bar's place. A saddled camel
  dashes forward the same way, then rests for a few seconds.
- **Armadillos** shed a scute every 5 to 10 minutes and curl up when undead come close, when
  whatever hurt them is near, or when a player sprints or rides past; curled up they take much
  less damage. Young ones can't be brushed.
- **Shears** take the pumpkin off a snow golem and the mushrooms off a bogged.
- **Allays** take the item you give them into their hand (an empty hand takes it back), gather
  that item up to a full stack (only with mobGriefing on), bring it to a note block played in the
  last 30 seconds or to you, and rest 3 seconds before gathering again. They heal over time, the
  player they like can't hurt them, they dance by a playing jukebox, and an amethyst shard given
  to a dancing allay makes a second one (then neither can for 5 minutes).
- **Camels** sit down and stand up now and then when left alone, and stand up when hurt or when
  their rider moves.
- **Cats** keep creepers away (creepers run from cats and ocelots), phantoms break off their dive
  near a cat (which hisses at them), and a tamed cat by your bed may leave you a gift in the
  morning. Skeletons run from wolves, and wild wolves run from llamas (the stronger the llama, the
  more surely).
- **Tamed cats like Java's** (Part 75): a tamed cat that hasn't been told to sit picks a seat now
  and then (the nearest closed chest, lit furnace or foot of a bed within 8 blocks, with nothing
  on top), sits there for one to three minutes, and keeps a chest shut while it sits on it. It
  lies down on beds a few blocks above or below it (Java's search for those skips the cat's own
  level). When you sleep, a cat nearby goes to the foot of your bed, rests its head for a moment
  and lies down purring, and that cat is the one that brings the morning gift. Strays come for
  fish but tamed cats don't. Cats, wolves and parrots follow you as in Java: they set off once you
  are 10 blocks away (parrots 5), stop within 5 (cats), 2 (wolves) or 1 (parrots), and from 12
  blocks they turn up next to you. You also sleep at the head of the bed now, whichever half you
  click.
- **Dying mobs** tip over onto their left side, quickly at first, as in Java (Part 75).
- **Beds and respawn anchors like Java's** (Part 76): you have to be within 3 blocks of a bed (2 up or down) to lie in
  it, with nothing over it that you could suffocate in (glass, leaves and the like don't count). The respawn point is
  set first; then you only fall asleep once the sky is dark enough (later on a clear evening than before, earlier in
  rain, any time in a thunderstorm) and with no monster within 8 blocks (5 up or down; slimes, phantoms and the like
  don't count, zombified piglins only when angry). A villager asleep in the bed is woken instead. In bed you look out
  from the pillow with the chat open and a Leave Bed button (Escape works too, and a hit wakes you); in the morning, or
  when you leave, you stand up beside the bed facing it and can move at once. Lying down at all resets the phantom
  timer. You respawn beside your bed, or beside your respawn anchor, which uses up a charge; if the bed is gone, the
  anchor empty or either one walled in, you come back at the world spawn instead.
- **Rails and minecarts like Java's** (Part 77): rails take their shape the way Java decides it: a new rail turns toward
  the rails beside it that have a free end, curves where it can (plain rails only), slopes up to a rail a block higher,
  and at a T-junction curves south-east first, or the other way round when powered; a plain rail at a junction switches
  when its redstone power changes. Powered and activator rails pass their power along to up to 8 more rails of their kind,
  and a sloping rail breaks when the block it climbs onto goes. Minecarts move like Java's: an empty cart loses 4% of
  its speed every tick and one with a passenger 0.3%, slopes and drops speed them up, powered rails push 0.06 a tick
  (or start a cart away from a solid block), unpowered ones brake, a furnace cart with coal pushes on at 0.2 blocks a
  tick, and activator rails tip riders out, light TNT carts and switch hopper carts off or on. A moving empty cart
  scoops up a mob it runs into, and a boat nobody steers takes in a mob that bumps it; a mob that gets out can't be
  taken in again for 3 seconds.
- **Boats like Java's** (Part 78): a boat slides according to what it is in or on: it keeps 90% of its speed a tick on
  water, 45% under water, and on land the friction of the blocks under it, from 60% on most blocks to 98% on ice and
  98.9% on blue ice. Rowed, it reaches 0.4 blocks a tick on water, 0.1 on dirt, 2 on packed ice and about 3.6 on blue
  ice, and its spin dies away at the same rate, so on ice it keeps turning. It floats with its bottom a little under the
  surface, lands on top of water it falls into, sinks when held under water (its rider floats off after 3 seconds),
  and keeps the rider's look within 105 degrees of its heading.
- **Dropped items like Java's** (Part 79): items slide with the friction of the block under them (far on ice), join up
  the way Java's do (every 2 ticks while moving, every 40 when still, with items right alongside, the smaller stack into
  the bigger and only when they fit in one), burn up in lava within two ticks, in fire within five and in soul fire
  within three, break on cacti, and fire-proof items such as netherite bob up and float in lava. An item caught inside
  a block works its way out through the nearest open side.
- **Experience like Java's** (Part 80): orbs come in Java's eleven sizes (1 up to 2,477 points), each drawn with its own
  icon (from your resource pack's orb sheet too: add a pack again if it was added before this update), see-through and
  pulsing between green and yellow. They pop out, fall slowly, rise in water, burn up in lava and fire, bounce a little
  when they land and fly to the nearest player within 8 blocks; orbs of a size sometimes join up. You collect one orb
  every other tick, from as far away as items (a block to each side of you), and what you pick up flies into you.
  Mending takes its share first, 2 points of repair a point, moving on to your next damaged mending item. Experience
  comes as orbs where Java's does: a furnace's when you take the output (or break the furnace), the Ender Dragon's
  raining down as it dies (12,000 the first time, 500 after), a villager's one orb per trade, with its new level coming
  2 seconds after you stop trading, and a grindstone's at the grindstone. A bottle o' enchanting gives 3 to 11 (usually
  about 7) and a spawner 15 to 43. Experience from advancements and commands doesn't mend anything.
- **Suffocation** (Part 81): with your head inside a block you could suffocate in (not glass, leaves and the like), you
  lose half a heart every half second, mobs too, so falling sand or gravel can bury you; inside a block the screen shows
  it close up and dark, as in Java.
- **Falling like Java's** (Part 82): a fall is measured the whole way down and its damage is rounded down, as in Java
  now: 3.5 blocks costs nothing, 4 or 4.5 blocks half a heart, 5 blocks a heart. Mobs take half the fall on beds and a
  fifth of the harm on hay bales and honey blocks too, and none on slime blocks. Falling sand and gravel no longer hurt
  anyone; a falling anvil does, a heart for every block it fell after the first (up to 20 hearts), and may land chipped
  or break; anvils keep their facing as they fall.
- **Soul sand and mud** (Part 83) are 2 pixels lower to stand on than they look, as in Java, so you, mobs, items and
  boats sink into them a little.
- **Parrots** are tamed with seeds one time in ten (cookies kill them), sit on their owner's
  shoulders until a jump, a swim, flying, sleep or a hit sends them off, dance by a playing
  jukebox and now and then imitate the monsters around them.
- **Axolotls** play dead when hurt in water (healing meanwhile, and nothing hunts them), give you
  Regeneration when you finish off what they were fighting, and dry out after 5 minutes out of
  water.
- **Bees** live in nests and hives (three at most) and work like Java's: out in the day, in at
  night and in the rain, home once they carry nectar or have searched for 3 minutes. A bee stays
  in 30 seconds, or 2 minutes when it brings nectar, which adds a level of honey. It works a
  flower within 5 blocks for 20 seconds to get nectar, remembers it, and grows up to 10 crops it
  flies over on the way home. A bee stings once (poison on normal and hard) and dies within a
  minute or so; hit one and the bees around that saw it come after you. Nests made with the
  world hold 2 or 3 bees.
- **Honey**: a full hive (honey level 5, shown on its front) gives a honey bottle or 3 honeycomb.
  Unless a lit campfire smokes it from below, the bees inside come out angry. Breaking a hive
  without Silk Touch lets them out angry too; with Silk Touch the hive keeps its bees and honey
  (the tooltip shows them). Comparators read the honey level.
- **Dispensers** do what Java's do: shears and glass bottles harvest full hives (honey farms
  work), shears shear sheep, mooshrooms, snow golems and bogged, bottles fill with water,
  honeycomb waxes copper, water bottles turn dirt into mud, glowstone charges respawn anchors,
  brushes brush armadillos; spawn eggs, armor stands, boats, minecarts and shulker boxes are
  placed; saddles, horse armor, carpets and chests go on animals and armor on players and armor
  stands; carved pumpkins and wither skeleton skulls finish golems and withers; bottles o'
  enchanting are thrown; flint and steel lights fire, portals, campfires and candles and sets off
  TNT; buckets empty (fish come out) or fill. Items drop out with Java's speed and spread.
- **Gold farms**: nether portals in the overworld now and then let out a zombified piglin (more
  often on harder difficulties).
- **Drowned and strays**: a zombie under water for 30 seconds shakes for 15 more and becomes a
  drowned (a husk becomes a zombie first); a skeleton that stays in powder snow for 7 seconds
  shakes and becomes a stray. They keep what they wear and hold.
- **Shulker boxes** keep their contents when placed again, and when one blown up drops.
- **Turtles** remember the beach they hatched on. Bred, one of the pair carries an egg home and
  digs 1 to 4 eggs into sand there; eggs crack and hatch (mostly in the hour before dawn), and a
  baby turtle drops a turtle scute when it grows up. Walking on eggs breaks them (sneak to be
  safe); zombies, husks, drowned and zombified piglins seek eggs out and stamp on them, so eggs
  lure them like in Java's gold farms.
- **Frogs** that breed lay frogspawn on still water beside land. It hatches 2 to 5 tadpoles after
  3 to 10 minutes; a tadpole grows into a frog after 20 minutes (a slime ball speeds it up), and
  the biome it grows up in decides its colour. Frogs eat small slimes and magma cubes, and a
  magma cube eaten by a frog leaves a froglight of that frog's colour.
- **Foxes** carry one item in their mouth (some spawn holding one) and pick up what they find,
  swapping it for food once they have eaten; they eat food they hold after 30 seconds (with its
  effects; chorus fruit teleports them). They pick sweet berries and glow berries, sleep in the
  shade by day and wake when anything comes near, stalk chickens and rabbits, crouch and pounce
  (landing nose first in snow), and run from players, wolves and polar bears. A fox bred by you
  trusts you and attacks whatever hurts you. Foxes have their own sounds now.
- **Villagers** carry up to 8 stacks of food and seeds, which they pick up off the ground or walk
  over to fetch. Bread counts as 4 food, carrots, potatoes and beetroots as 1. Two villagers with
  12 food each court when they have nothing else to do, eat 12 each, and have a baby if a bed is
  free within 48 blocks (the baby takes that bed); then they wait 5 minutes. Idle villagers walk
  up to each other and pass on what they have heard, and one with plenty of food throws some to a
  farmer or to one that is short of it, so villager breeders with a farmer work as in Java.
- **Farmers** walk their farmland, harvest ripe crops and replant them from what they carry, use
  bone meal (you see it in their arms), and at their composter bake bread out of wheat and
  compost the seeds they don't need.
- **Gossip**: villagers remember who traded with them, hurt them, killed one of them where they
  could see it, or cured them, and tell each other (a cure stays with the villager cured). It
  fades day by day. Prices follow it, and also rise for trades that sold out and fall back when
  they go unused; villagers restock at their job site up to twice a day. An iron golem turns on a
  player that the villagers near it think very badly of.
- Hold an emerald (or anything a villager's trades cost) near a villager and it shows you what it
  would give for it. A full composter takes a second before its bone meal is ready. Witches drink
  water breathing, fire resistance, healing and swiftness when they need them, holding the bottle
  at the nose. The wandering trader drinks invisibility at dusk and milk in the morning, and you
  can see the bottle while it is invisible.
- **Goats** ram the nearest living thing they can see (players only in survival or adventure)
  every 30 seconds to 5 minutes, screaming goats every 5 to 15 seconds: they back off 4 to 7
  blocks in a straight line, lower their head and charge, and the hit throws you far (half as
  far if you block it with a shield). A goat that charges into stone, logs, packed ice or some
  ores snaps off a horn, always the same kind of horn for the same goat. Kids have no horns.
  Goats leap up to 5 blocks to ledges they can't walk to, and falls only hurt them beyond 13
  blocks.
- **Striders** shiver and turn purple out of lava, walking slower, take damage from water and
  rain, and make their own way back to lava. Riding a pig or a strider, right click with the
  carrot or warped fungus on a stick for a burst of speed; it wears out the stick, which leaves
  a fishing rod when it breaks.
- **Dolphins** go up for air every few minutes, dry out on land, swim alongside you when you
  sprint-swim and give you Dolphin's Grace, play with items in the water, leap at the surface,
  follow boats and fight back together. Feed one a fish and it leads you to the nearest
  shipwreck or ocean ruin.
- **Sniffers** sniff the air, walk off to a spot they choose and dig up a torchflower seed or a
  pitcher pod, never in the same place twice, then rest for 8 minutes. Bred, they lay a sniffer
  egg, which cracks twice and hatches after about 20 minutes (10 on a moss block); snifflets
  take 40 minutes to grow up.
- **Crouching, swimming and crawling** work as in Java: crouching makes you 1.5 blocks tall so you
  can sneak under low gaps, and you stay crouched where you can't stand up. Sprint under water
  and you swim, lying flat and heading wherever you look, faster than paddling; where even
  crouching doesn't fit (under a trapdoor, through a one-block hole) you crawl, slowly. Water
  slows you down and you sink slowly, the same as in Java, and you can see the swimming strokes
  in third person.
- **Mobs ride mobs**: chicken jockeys (baby zombies, husks, drowned, zombie villagers and
  zombified piglins on chickens), spider jockeys with skeletons, strider jockeys with zombified
  piglins (or baby striders), and raid ravagers carrying pillagers, vindicators and evokers. The
  rider steers its mount toward whatever it is after; riders get off when the mount dies or
  their head goes under water, and a mount and its rider are saved together.
- **Skeleton trap horses**: lightning in a thunderstorm sometimes leaves a skeleton horse
  behind. Walk within 10 blocks of it and lightning flashes: four skeleton horsemen with
  enchanted bows and iron helmets appear.
- **Leads like Java's**: a led animal walks to within 2 blocks of you, gets pulled along from 6
  blocks and the lead snaps (and drops) past 10. The rope is drawn between you. Right click a
  fence while leading animals to tie them to a knot on it; right click the knot to tie more or to
  set them free. Leads are saved with the world, even on fences.
- **Llamas**: a llama joins the back of a caravan behind a llama on a lead (up to 10), spits at
  whatever hurts it and at wild wolves, and a herd shares one coat. Trader llamas are tied to
  their wandering trader and defend it.
- **Pandas with genes and moods**: each panda carries two genes (brown and weak only show in
  pairs) that cubs inherit. They sit up to eat bamboo and cake, lazy ones lie on their backs,
  playful ones roll over, cubs sneeze, worried ones hide from players and thunderstorms, and
  aggressive ones fight back together. They won't breed without bamboo nearby.
- **Rabbits, sheep and polar bears**: rabbit coats by biome, rabbits raiding ripe carrots; lambs
  get the dye colour their parents mix into, killed sheep drop their wool, jeb_ shines in every
  colour; polar bears guard their cubs, hunt foxes and rear up before they strike.
- **Piglins like Java's**: gold you drop near a piglin gets picked up and admired for about 6
  seconds; an ingot (also one handed over) is then traded for something from Java's bartering
  table, thrown your way. Hit one while it admires and the gold is gone. Wear at least one piece
  of gold armor or they attack you; opening chests and other containers or breaking gold near
  them makes every piglin around angry for 30 seconds. They hunt hoglins and celebrate, keep
  away from soul fire and zombified piglins, and young piglins never carry weapons.
- **Piglin brutes, hoglins and zoglins**: brutes attack any player, gold or not, and stay near
  where they spawned. Hoglins toss whatever they hit into the air, avoid warped fungus, portals
  and respawn anchors, and flee from groups of piglins; zoglins attack everything but creepers.
  Outside the Nether all of them shake and turn into zombified piglins or zoglins after 15
  seconds.
- **Endermen like Java's**: look one in the eyes (a carved pumpkin on your head prevents it) and
  it screams, shakes and comes after you, much faster than you can run. While you keep watching
  it from close by it stands still, and if you are within 4 blocks it teleports away; when you
  run more than 16 blocks off it teleports after you. It stays angry for half a minute after
  losing you. Arrows, snowballs and other projectiles never hit it (it teleports first), water
  and rain hurt it and make it teleport around, and by day it eventually gives up. Endermen pick
  up and put down dirt, sand, flowers, pumpkins, TNT and the other blocks Java lets them carry,
  hold them in front of them, and drop them when killed.
- **Endermites** come with 1 in 20 thrown ender pearls, live 2 minutes unless named, and
  endermen go after them.
- Splash water bottles put out burning mobs and hurt endermen, blazes, striders and snow golems.
- **Regional difficulty**: as in Java, the longer you spend around a place, the world's age and
  the moon make it harder. F3 shows it as Local Difficulty. It decides how often monsters wear
  armor and carry weapons and how many of them can pick things up or break doors.
- **Zombies like Java's**: they walk at Java's speed and baby zombies are much faster. On Hard
  a hurt zombie can call another of its kind out of the dark nearby (even with the blow that
  kills it), and zombies that can break doors bang on wooden doors and break them after 12
  seconds. Hitting one brings the others around it after you. A zombie that stays under water
  for 30 seconds starts to shake and becomes a drowned; husks become zombies. A helmet keeps the
  sun off (and wears out instead), and baby zombies burn in daylight too.
- **Monsters lose track of you like in Java**: they need to see you to come after you, give up
  once you're out of sight for 3 seconds, and only chase you as far as Java lets them (35 blocks
  for zombies, 16 for skeletons, creepers, spiders and most others).
- **Skeletons like Java's**: they keep their distance and circle you, draw the bow for a second
  and shoot every 3 seconds (2 on Hard) with Java's aim, which misses more than before. Stray
  arrows slow you for 30 seconds and bogged arrows poison you. Skeletons hide from the sun
  under cover, run from wolves, and one stuck in powder snow turns into a stray.
- **Creepers like Java's**: once a creeper starts to hiss you have to get more than 7 blocks
  away (or out of sight) to stop it. It swells up and flashes white before it explodes, falls
  make it hiss sooner, and a charged creeper's blast drops the head of the first zombie,
  skeleton, creeper or piglin it kills.
- **Spiders like Java's**: they only pick a fight in the dark (below light 12), leap at you
  from 2 to 4 blocks away and walk through cobwebs, which slow down every other mob.
- **Slimes and magma cubes like Java's**: their size (1, 2 or 4) sets their health, damage and
  speed, and they're now drawn at that size; they hop with Java's timing and distances, stretch
  as they jump and squash as they land (magma cubes come apart in the air), and hurt you by
  touching you (the tiniest slimes don't). A big one splits into 2 to 4 smaller ones when its
  body vanishes, and they keep its name.
- **Silverfish** call more silverfish out of nearby infested stone when hurt and hide in stone
  again when left alone. **Witches** walk at Java's speed and drop Java's loot.
- **Phantoms like Java's**: they circle high above, pick the player they can see, and every 8
  to 11 seconds swoop straight at you, bite and climb back up. Bumping into something, getting
  hit or a cat nearby breaks off the swoop (the cat hisses). Hiding under a roof makes them lose
  you. They speed up on straight runs and turn slowly, flap with a sound you can hear, leave
  grey specks behind their wings and burn in daylight.
- **Ghasts like Java's**: they drift around, pick a player no more than 4 blocks above or below
  them, cry out as they charge and fire every 3 seconds while they can see you. Fireballs (theirs
  and blazes') start slow and speed up the farther they fly, trail smoke, and still bounce back
  when you hit them.
- **Blazes like Java's**: they walk, float down slowly and rise to stay above you, light up for 3
  seconds, then shoot three fireballs in quick succession and rest for 5 seconds. Their fireballs
  set you on fire and light the ground where they land.
- **Guardians like Java's**: they lock on to players, squid and axolotls with a beam you can see
  turning from purple to gold, and hit when it's charged (4 seconds, 3 for elder guardians).
  Hitting one while its spikes are out hurts you back, and on land they flop around.
- **Illagers like Java's**: pillagers walk up, load their crossbows, take aim and shoot, then load
  again; vindicators run you down with their axes (and in a raid break wooden doors on Normal and
  Hard). Evokers keep their distance and stop to cast: vexes, rows or rings of fangs that snap
  shut a moment after they appear, and with nothing to fight they turn blue sheep red. Vexes dart
  at you through walls until they waste away; ravagers crash through leaves, and if your shield
  stops one, it may be stunned and then roar, throwing everything around it back.
- Mobs that hurt you now scale with the difficulty for arrows, tridents and magic too (on Easy
  never more than the hit itself), and a second, stronger hit during the moment you're
  invulnerable deals the difference, like in Java. Cobwebs hold flying mobs as well, and mobs
  with Weaving get through them twice as fast, like players do.
- **Shulkers like Java's**: they peek out now and then, and open up to shoot bullets that zigzag
  towards you a block at a time and make you float. Shut, they're armoured and arrows bounce off;
  hurt badly they may teleport, and one hit by a shulker bullet can leave a copy behind. You can
  stand on them, and an opening shulker lifts you up.
- **Drowned like Java's**: by day they only go after you in the water (and head back to it), at
  night they come ashore. They sink and walk the bottom unless they're chasing something in the
  water, and the ones with tridents hold them up and throw one every 2 seconds.
- **Breezes like Java's**: they breathe in and leap to land behind you, then fire a wind charge;
  too close and they slide away. Arrows and other projectiles bounce off them, but not wind charges.
- **Iron golems like Java's**: a hit does 7.5 to 21.5 damage and throws you up; they chase at Java's speed,
  go after monsters even behind walls (never creepers), and stay angry at a player who hit them for 20 to 39
  seconds. One you built never turns on you. Iron ingots repair them (25 health each), they creak as they crack,
  and now and then they hold out a poppy to a villager.
- **Snow golems like Java's**: they throw a snowball every second at monsters in sight (creepers too) and leave a
  trail of snow (unless mobGriefing is off). They melt in deserts, badlands, savannas and the Nether, and water and
  rain hurt them.
- **Animals move like Java's**: pigs, cows, sheep, chickens, goats, horses, llamas, cats, wolves, villagers, piglins,
  hoglins and more walk, run in panic, follow food and their parents at Java's speeds (a scared cow is fast), and babies are no faster
  than adults. Hit an animal and it dashes about for a couple of seconds like in Java.
- **Horses like Java's**: every horse has its own health (15 to 30), speed and jump, and foals get theirs from their
  parents, so you can breed better horses. Riding one is as fast as in Java (about 10 blocks a second for an average
  horse); a horse and a donkey make a mule, and only tamed ones at full health breed.
- **The Ender Dragon like Java's**: it circles the island along Java's flight paths, swoops past to shoot dragon
  fireballs that leave clouds of dragon's breath, and lands on the portal to roar and breathe on you; hit it hard
  while it sits and it takes off again. Its head takes full damage, the rest of it a quarter; arrows bounce off it
  while it perches; its wings throw you away and its bite hurts. The nearest crystal heals it with a beam, and
  breaking that crystal hurts it and makes it come after you. It smashes through blocks other than obsidian, end
  stone and the like.
- **Fish like Java's**: cod, salmon, tropical fish and pufferfish swim at Java's speeds, dart away from players and
  when hit, and flop about on land until they dry out. Cod, salmon and tropical fish form schools that follow a
  leader. Pufferfish puff up halfway when something comes near and fully after two seconds, sting with poison
  while puffed, and shrink back once left alone.
- **The Wither like Java's**: the soul sand T needs its two lower corners empty and can stand, lie down or hang
  upside down (iron and snow golems can be built lying down too). A built Wither charges for 11 seconds, then
  blows up and hunts the nearest living thing that isn't undead. It hovers 5 blocks over its target until half
  health, then comes down to its level. Each head fires on its own, and idle side heads send blue skulls that
  break almost anything. When hurt it smashes the blocks around it. Skulls go through armor the way Java's do,
  wither what they hit and leave wither roses where they kill. Its boss bar darkens the world. One from a spawn
  egg starts fighting straight away.
- **Packs from newer versions**: resource packs made for versions after 1.21, such as 26.x template packs,
  work without missing or mixed-up textures. The game knows their new file names and layouts: cow, pig and
  chicken variants, cats, frogs, llamas, pandas and other renamed mobs, armor, trims, saddles and horse, wolf and
  llama armor from the equipment folders, the moon's eight separate pictures, and renamed blocks such as the
  chain and the pillars. Mobs are drawn from both sides like Java's, so thin parts such as a chicken's legs show
  the way the pack paints them. Allays now have their own look instead of being invisible.
- **Pistons like Java's**: a piston moves up to 12 blocks, and slime and honey blocks drag the blocks
  around them along (but not each other) and stick to whatever they touch, the ground included. Glazed
  terracotta can be pushed but not pulled; obsidian, anvils, extended pistons and blocks that hold things
  (chests, furnaces, hoppers ...) don't move; plants, torches, redstone dust, leaves and melons break. Blocks slide
  for 2 ticks before they land, and a sticky piston powered for only a moment leaves its block behind. Entities in
  the way are pushed along, slime blocks launch them, and honey blocks carry what stands on them.
- **Camel and strider saddles**: a saddled camel wears Java's saddle with its rug, a bridle and, while ridden,
  reins; a saddled strider wears its saddle. Resource packs' saddles are used, including the separate saddle
  textures of newer packs.
- **The deep dark like Java's**: every vibration has Java's frequency, from footsteps (1) to explosions and
  deaths (15). Sculk sensors hear it within 8 blocks (calibrated sensors 16), and it reaches them at a block a
  tick. Wool in the way stops it, sneaking hides footsteps, landings and shots, and wool or carpet underfoot
  muffles steps. A sensor's signal is weaker the farther away the noise was, a comparator reads its frequency,
  and amethyst next to it rings on. A calibrated sensor fed a signal on the side that faced you when you placed
  it only hears that frequency. Shriekers answer the click of a sensor near them, or you standing on them: warnings
  come at least 10 seconds apart, a warden digs out at the fourth, and none come while a warden is close. The
  warden gets angry at whatever it hears or sniffs out (players first), roars, then punches; its sonic boom goes
  through walls, but not in the first 10 seconds of a fight or while it can keep hitting. It digs back down after a
  minute without anger. Saddled horses, donkeys and mules wear Java's bridle, with reins while ridden.
- **Sculk spreading like Java's**: when anything dies within 8 blocks of a sculk catalyst, the nearest catalyst
  blooms and takes its experience (no orbs drop) as a charge that creeps out from where it died. Sculk veins turn
  the stone, deepslate, dirt, sand, terracotta and the like they cover into sculk and grow over the faces around
  it, and on sculk the charge now and then raises a sculk sensor, or sometimes a shrieker that can't call a
  warden, at least 4 blocks from the catalyst and never crowded together. The bigger the death, the farther it
  spreads; a player's death near one feeds it too.
- **Bats and squid like Java's**: bats hang upside down from the ceiling and drop off to flutter about when you
  come within 4 blocks, when hit or when their ceiling goes, darting from spot to spot until they roost again.
  Squid swim in strokes of their tentacles, pushing off and gliding, tipping toward where they go and spinning as
  they push. Hit one and it squirts a cloud of ink and swims away from you; out of water it flops and sinks. Glow
  squid glow and shed specks of light, and go dark for a few seconds when hurt.
- **Farming like Java's**: crops grow at Java's rates, which depend on the farmland under and around them (wet
  farmland counts three times as much as dry) and slow down when the same crop is planted on all sides, so rows
  grow faster than solid blocks; beetroots and torchflowers grow a third slower. Crops, stems and berry bushes keep
  growing at night under the open sky. Sugar cane and cactus grow a block every 16 random ticks, and a cactus that
  grows next to a block breaks off. Saplings grow in two steps, azaleas only with bone meal, and nether wart in any
  light. Farmland dries out step by step away from water and rain. Bone meal gives crops 2 to 5 stages, but does
  nothing to nether wart, sugar cane or cactus.
- **Little things that felt wrong, fixed**: stepping up now tries the lowest ledge first, like Java, so you (and
  villagers) can walk from a path block into a house even with the door's lintel right above your head. Mobs only
  jump when Java's mobs would (a ledge higher than a step, close by), so cows and sheep no longer hop over path blocks,
  farmland or carpets, and villagers walk through their doors. Mining adds up the damage of each tick as things are at
  that moment, so a block you started hitting in mid-air or in water speeds up as soon as you stand on the ground, and
  switching tools starts over; blocks that break at once can be broken one per tick while you hold the button, and
  there is Java's short pause after a block that took longer. Punching a note block plays it, and a dragon egg jumps
  away. Beds are drawn like the bed models of newer versions, a texture per face, so resource packs texture them:
  packs from 1.21 and before (one bed texture per color) and newer packs (one texture per face) both work.
- **Bug fixes**: grass blocks show the green grass edge on their sides again, with or without a resource pack (it was
  drawn in the same place as the dirt and lost every time). The chat can't get stuck any more: if you leave the tab or
  click the game while it's open, Escape still closes it, Enter still sends, typing goes back into the box, and a click
  never catches the mouse while it's open. The air bubbles go away once your air is full again (they used to stay on
  screen until the game was restarted) and show while your head is under water, like Java. Checked every block
  against the default 26.2 resource pack's own models: the crafting, cartography, fletching and smithing tables now have
  the right texture on each side, the jukebox and quartz block have the right bottoms, and slime and honey blocks have
  their inner cube inside the see-through shell, like Java.
- **Terrain like Java Edition 26.3**: caves and ravines now carve the way 26.3 carves them (through every block but
  bedrock, each column from the top down, so the grass and dirt at a cave mouth come out like Java's), the copper and
  iron ore veins and the bedrock floor follow 26.3's rules, snow and stone sit on the same steep slopes as in Java
  (the slope test looked along the wrong axes), and the grass under shallow water follows 26.3's rule. Two new stones
  from 26.3, **sulfur** and **cinnabar**, are in the creative inventory; they will start appearing in the world with the
  sulfur caves biome. New chunks of worlds made before this version use the new rules, so a cave can end in a straight
  wall where old and new chunks meet.
- **The biomes of Java Edition 26.3** (Part 64): Java seeds now give 26.3's biome layout, with its three new biomes
  where Java has them. **Pale gardens**: grey-green pale oaks with moss hanging from their leaves and trunks, pale
  moss on the ground, and **creaking hearts** inside some trunks (uprooted unless pale oak logs hold them at both
  ends, dormant by day, glowing awake at night, when they call up a creaking: see Part 66); **eyeblossoms** open as night
  falls and close at dawn, and each one that turns sets off the ones around it. **Dappled forests**: orange grass
  under red, orange and yellow **poplars**, leaf litter, fallen poplar logs with **shelf mushrooms** (bouncy to
  land on, bigger with bone meal), red shrubs. **Sulfur caves**: bands of **sulfur** and **cinnabar**, **sulfur
  spikes** pointing up and down like dripstone, and pools over **potent sulfur**, which gives off a gas that makes
  whoever breathes it at the surface sick, and over magma erupts every half minute or so (over lava all the time),
  pushing up whatever stands in the water above it. The new blocks are all in the creative inventory with their
  26.3 recipes and drops: the **pale oak** and **poplar** wood families (logs, wood, planks, stairs, slabs, fences,
  gates, doors, trapdoors, plates, buttons, signs, hanging signs, saplings, boats and chest boats; the saplings
  grow Java's trees, see Part 67), **pale moss** and its carpet (which climbs the
  walls beside it), **pale hanging moss**, the **resin** family (clumps, block, bricks with stairs, slabs, walls and
  chiseled bricks, the resin brick smelted from a clump), **golden dandelions**, the **sulfur** and **cinnabar**
  families (polished, bricks, chiseled, with stairs, slabs and walls) and **potent sulfur**. Pointed dripstone now
  shows all five of its thicknesses like Java's. New chunks of worlds made before this version follow the new
  biomes, so a biome can change where old and new chunks meet.
- **Trees, plants and ores like Java Edition** (Part 63): new chunks are decorated the way Java Edition decorates
  them, so a seed's trees, flowers, grass, ores, lakes, geodes, dungeons and cave decorations stand where they stand
  in Java Edition 26.3 (see *Java Edition terrain from Java seeds*). This brings Java's dripstone caves (pointed
  dripstone, clusters and big dripstone columns), lush caves (moss, clay pools with dripleaves, azalea trees over
  rooted dirt and hanging roots, cave vines, spore blossoms), geodes, icebergs with blue ice, ice spikes and coral
  reefs. The plants of 1.21.5 are new blocks: **bushes**, **firefly bushes** (fireflies come out around them when
  it's dark), **short and tall dry grass**, **leaf litter**, **wildflowers** and **cactus flowers**, in the creative
  inventory and in the world where Java grows them. Leaves now stay on as long as a log is within 6 blocks through
  the leaves, as in Java (they used to fall more than 4 blocks away, so big trees lost part of their crowns).
  To decorate a chunk the way Java does, Blockcraft needs the terrain of the chunks around it, so new chunks take
  longer to make than before: the ground around you appears about as quickly as it used to, but farther chunks fill in
  more slowly when a world is first loaded (each chunk's terrain and decoration is worked out once and shared between
  the background workers).
- **Villages like Java's** (Part 65): villages and pillager outposts now shape the land around their buildings
  the way Java Edition does, with the terrain adaptation Java uses for them: the ground rises in a smooth mound under
  a house on a slope and opens up above one set into a hillside, where houses used to stand on cobblestone pillars or
  in boxes cut out of the hill. Like Java's, a village is laid out on the water's surface when it starts by a lake or
  a river, so it no longer shrinks to a lone well there; streets cross rivers on planks and stop at the shore of wider
  water. Streets keep a few grass blocks in them like Java's (one in ten in the plains, one in five in savanna, taiga
  and snowy villages; in snowy villages they get a layer of snow). Farms are sown with wheat, with carrots, potatoes and beetroots
  (or melons, pumpkins and potatoes, depending on the style) mixed in at Java's odds for each style, all just
  planted. A house's villager is a nitwit one time in twelve and a baby one time in twelve, as in Java. And one
  village in fifty is **abandoned**, where Java has its abandoned villages: zombie villagers instead of villagers
  (they never despawn), no iron golem or cats, no doors or torches, cobwebs, mossy cobblestone and brown, grimy
  windows, at the odds of Java's abandoned villages. New chunks of worlds made before this version follow the new
  rules, so the ground can step where old and new chunks meet near a village.
- **The creaking** (Part 66): at night an awake creaking heart calls up a creaking when you come within 32 blocks, a
  tall, bark-skinned figure that stands somewhere up to 16 blocks from its heart. It can't move while you look at it
  (within about 60 degrees of where you look, with nothing solid in the way; glass doesn't hide it), and looking at it
  from within 12 blocks wakes it up: its eyes light up and, the moment you look away, it comes for you, fast, and hits
  for 3 hearts' worth every 2 seconds. Once it's awake, a carved pumpkin on your head stops your looks from freezing it.
  You can't hurt a heart's creaking: a hit only makes it twitch, sends a trail of sparks back to its heart and, while the
  heart is awake, grows two or three resin clumps on the pale oak logs around the heart. Break the heart to get rid of it:
  the creaking shakes for two seconds and crumbles into bits of wood. It also crumbles at dawn and when it strays more
  than 34 blocks from its heart. A creaking from the new spawn egg is an ordinary monster that one hit kills. Its model
  and textures follow Java's, so a resource pack's creaking (with its glowing eyes) shows on it.
- **Saplings grow Java's trees** (Part 67): a sapling now grows exactly the trees Java Edition grows from it, built by
  the same code that places the world's trees: an oak becomes a fancy oak one time in ten, and with a flower within two
  blocks the tree carries a bee nest with bees one time in twenty (birches and cherries too); four spruce or jungle
  saplings in a square grow a giant spruce, a giant pine or a giant jungle tree; dark and pale oaks need a square of four;
  mangrove propagules grow mangroves (tall ones most of the time) with their roots, moss and hanging propagules; azaleas
  grow azalea trees over rooted dirt; poplar saplings grow one of the three poplars. As in Java, a sapling that has no
  room for its tree simply stays a sapling.
- **Skies like Java's biomes** (Part 68): the sky takes the colour of the biomes around you, as in Java Edition 26.3:
  paler over deserts, savannas and badlands, bluer over snow and peaks, and grey over the pale garden; the fog is the usual
  light blue, or a biome's own: grey-brown in the pale garden, misty in the dappled forest, yellow-green in the sulfur caves.
  Colours blend smoothly across biome borders, and dim through the day as Java's do (a black sky at night). Under water the
  fog is the biome's water colour (a deep navy most places, greener in swamps, lighter blue in cherry groves) and your eyes
  get used to it: at first you see about 24 blocks, after half a minute 96. Water in deserts, badlands, savannas and most
  snowy biomes is now the ordinary blue it is in Java. With a resource pack, the decorated pot's top and bottom, the
  lever's base and the barrier now use the pack's own textures too.
- **Copper tools and armor** (Part 69, as in Java Edition 1.21.9): copper swords, pickaxes, axes, shovels and hoes
  sit between stone and iron (190 uses, they mine what stone tools mine but faster, and a copper sword does 5 damage), and
  copper armor between leather and chainmail (10 armor points for the set). They're crafted from copper ingots, repaired
  with them, and melt back down into copper nuggets in a furnace or blast furnace; nine nuggets make an ingot. A trim of
  copper on copper armor shows in a darker copper, and there's copper horse armor (4 points). With a 1.21.9 or newer
  resource pack, the pack's copper textures show on the items and on whoever wears them. Every mob in the game that has
  a spawn egg in Java now has one here too (24 more, from the camel to the zombie horse).
- **Moving like Java** (Part 69): walking, sprinting and sneaking now go exactly Java's speeds (4.317, 5.612 and 1.295
  metres a second), and sneaking diagonally is faster than sneaking straight, as in Java. Sprint-jumping was much too
  fast (8.9 m/s): the ground's grip now counts for the tick you jump from and not for the tick you land on, as in Java, so
  it's Java's 7.1 m/s. Slime blocks are slippery and slow to walk on, and bounce you back up as high as Java's do
  (sneaking onto one hurts like any other fall); beds bounce you too and only half the fall counts on them (the harm was
  halved instead before); honey blocks halve only the jump itself, not what Jump Boost adds.
- **Items and blocks checked against 26.3**: every item's durability, damage, attack speed, armor, stack size,
  enchantability and food were compared with Java Edition 26.3's, and the rarity colours of item names now match it
  (the elytra, dragon head and dragon egg are epic, heads, sherds and the conduit uncommon, the beacon and enchanted books
  rare, horse armor and the end crystal common, and an enchanted book's name no longer turns purple); honey bottles are
  drunk rather than eaten and can be drunk when full; dropped netherite blocks and ancient debris don't burn; the 26.3
  blocks (sulfur, cinnabar, resin bricks, pale oak and poplar wood) resist explosions as they do in Java.
- **Recipes like 26.3** (Part 70): every crafting, smelting, blasting, smoking, campfire and stonecutter recipe now gives
  what Java Edition 26.3 gives for the items Blockcraft has. The mace can finally be crafted (its recipe never matched
  before); andesite, diorite and granite are made from cobblestone and quartz; a lead takes five string and no slime ball;
  name tags (paper and a nugget) and saddles (three leather and an iron ingot) can be crafted; a lodestone needs an iron
  ingot; any two mushrooms make stew; a dye recolours wool, carpets and beds of any colour; smithing templates are copied
  with seven diamonds; six banner patterns are made from paper and a charge; waxed copper is cut and shaped like plain
  copper; the stonecutter cuts deepslate and stone into their cobbled kinds; smelting leaves gives leaf litter and horse
  armor melts down into nuggets.
- **Chest loot like 26.3** (Part 70): the chests of dungeons, temples, strongholds, shipwrecks, ruined portals, bastions,
  the End and the ancient city hold what 26.3's do: leather where saddles were (saddles are crafted now), copper horse
  armor, smithing templates two at a time, random enchanted books at Java's odds (curses as likely as the rest) and
  suspicious stews with their effects.
- **Trades like 26.3** (Part 70): villagers trade from 26.3's trade sets. Cartographers sell maps to the villages of
  other biomes (a desert cartographer never sells a desert village map), to jungle temples and swamp huts, to ocean
  monuments and trial chambers, and banners of every colour; shepherds and masons offer every colour of wool, carpet,
  bed, banner and terracotta; leatherworkers' armor comes dyed; master librarians sell candles instead of name tags;
  fishermen buy boats. The wandering trader buys water bottles, buckets of water and milk, baked potatoes and hay, and
  sells 26.3's goods: dyes, flowers, saplings and logs of every tree, moss, coral and more.
- **Bundles** (Part 71): the bundle and its sixteen dyed colours, crafted from string and leather and dyed with any dye
  (what is inside stays). A bundle holds one stack's worth of mixed items: 64 of a kind fill it, items that stack to 16
  take four times the room, a tool or other unstackable item fills it alone, a bundle inside takes a sixteenth plus what it
  holds, and shulker boxes don't go in. In the inventory, with a bundle in hand, left click a stack to put it in and
  right click an empty slot to take one out; with a bundle in a slot, left click it holding a stack to put that in, or
  right click it with an empty hand to take one out. The mouse wheel over a bundle picks which stack comes out next. Its
  tooltip shows what is inside and how full it is, and using one throws its stacks out one after another.
- **Wool and concrete stairs and slabs** (Part 71): every colour of wool and concrete now has stairs and slabs as in
  26.3, crafted and (for concrete) stonecut like other stairs and slabs, in the Colored Blocks tab.
- **Dropping with Q keeps an item's data** (Part 71): an item thrown with the drop key keeps its enchantments, name,
  damage and contents (it used to come out as a plain copy).
- **The Copper Age's blocks** (Part 72): copper torches (a copper nugget over coal or charcoal over a stick make four)
  burn with a green flame; copper lanterns (eight copper nuggets around a copper torch), copper chains (an ingot between
  two nuggets) and copper bars (six ingots make sixteen) come in all four stages of weathering, and lightning rods now
  weather too. Each has a waxed twin made with honeycomb, an axe scrapes a stage off, and lanterns and hanging signs hang
  from copper chains as well. The chain is called the iron chain now, as in 26.3 (chains in older worlds and inventories
  carry over).
- **Netherite horse armor** (Part 72): diamond horse armor upgrades at the smithing table with a netherite upgrade
  template and a netherite ingot: 19 armor points, 3 toughness and a tenth of knockback resistance, and it doesn't burn.
  Horse armor's toughness now counts too (diamond's 2).
- **Copper weathers like Java's** (Part 72): a random tick on unwaxed copper tries about one time in eighteen; then the
  copper looks at the weathering copper within four blocks: if any of it is fresher, nothing happens, and otherwise the
  more of it is already further along, the likelier it is to move on (fresh copper a quarter less likely still). Lightning
  striking weathering copper, or the copper a lightning rod stands on, polishes it back to new and wanders through the
  copper around it, taking a stage off as it goes.
- **The world around you moves like Java's** (Part 73): every tick the game picks 1,334 random blocks around you as Java
  does (most of them close by) and lets each make its particles and sounds. Torches smoke and flicker (on walls too),
  redstone torches, powered dust, repeaters and levers give off red specks, lit furnaces puff smoke and flame from their
  fronts and crackle, smokers smoke and brewing stands steam, candles burn with little flames, end rods shed sparkles.
  Lava pops, spits embers that trail smoke and rumbles; water seeps through ceilings and drips (lava too), pointed
  dripstone drips from the water or lava above it, wet sponges and crying obsidian weep. Leaves let fall a leaf now and
  then (tinted like the leaves; cherry petals drift off, pale oak and poplar leaves swirl) and drip in the rain, spore
  blossoms shower green specks, mycelium smokes faintly. Fire smokes and crackles, nether portals swirl and hum, ender
  chests and end gateways shimmer, charged respawn anchors draw particles up, spawners smoke and flicker while you are
  near, campfires send up Java's big puffs (a tall signal column over a hay bale) and wisps off the food on them, and bookshelves send glyphs flying into an enchanting table's book. Crimson and warped forests fill with
  drifting spores, the soul sand valley with ash and the basalt deltas with white ash, at Java's odds.
- **Enchanting table shelves count like Java's** (Part 73): each of the 32 spots two blocks out counts when the block
  halfway to the table, on the shelf's own level, is air or something as thin (grass, snow, water...). The old count
  wanted both levels clear and looked through the corners.
- **Redstone ore glows when touched** (Part 73): punching it, walking on it (not sneaking; mobs and items lying on it
  too) or clicking it lights it up (light 9, with red specks on its open faces) until a random tick puts it out, as in
  Java; clicking it with a block in hand still places the block.
- **Pack smoke the right way round** (Part 73): with a resource pack, smoke and other puffs now shrink as they fade like
  Java's (the pack's frames were taken in the reverse order).
- **Large chests** (Part 74): two chests side by side join into a large chest of 54 slots, the way Java decides it: a
  chest placed next to a lone chest facing the same way joins it; sneaking keeps it alone, or joins it to the side of the
  chest you click (taking that chest's facing); trapped chests only join trapped chests. The two halves are drawn as one
  long chest with a single lock (from resource packs too), open as one "Large Chest" screen, and hoppers, hopper
  minecarts, droppers, crafters and comparators treat them as one container; breaking a half leaves the other a single
  chest with its own items. Hoppers and droppers also fill containers nobody has opened yet.
- **Chest lids and trapped chests like Java's** (Part 74): a chest, large chest or ender chest won't open under a solid
  block (anything that carries redstone power; glass, slabs and the like don't stop it), and a chest or large chest won't
  open while a cat sits on it (Part 75). A trapped chest gives a redstone signal while you look inside, and powers the
  block under it.
- **Explorer maps as 26.3 items** (Part 74): the maps cartographers sell and shipwrecks hide are items of their own, as
  in 26.3 (Ocean Monument Map, Woodland Mansion Map, Buried Trial Chambers Map, Jungle Pyramid Map, Swamp Hut Map, the
  five village maps, Buried Treasure Map and the rest), each with its own picture. They work like any filled map: they
  copy as themselves at the crafting or cartography table and lock with glass, but only a plain map zooms out.
- **Armor trims**: a smithing template, a piece of armor and a trim material at the smithing
  table give the armor one of the 18 trim patterns in the material's colour (iron, copper, gold,
  lapis, emerald, diamond, netherite, redstone, amethyst or quartz; a trim of the armor's own
  material is a darker shade). Trims show on the armor worn by you, mobs and armor stands, on
  the armor's icon and in its tooltip. The smithing table shows an armor stand wearing the
  result, pictures of what goes in each empty slot, and a crossed-out arrow when the three
  items don't go together. The player in the inventory wears your armor too.
- **Banner shields**: craft a shield with any banner to put the banner's colour and pattern
  layers on the shield (it is then called e.g. *Red Shield*). Shields are drawn as Java's 3D
  shield: in your hand in first and third person (raised while blocking), on the ground, in item
  frames and in the inventory.
- **Banner markers on maps**: use a filled map on a banner inside the map's area to mark it in
  the banner's colour, with its name if you renamed it at an anvil; use it again to take the
  marker off. A marker disappears once its banner is broken and the map is updated there.

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

     Any version from 1.13 onwards works, including the 26.x versions; newer versions cover more blocks. The pack shows up as
     "Minecraft 1.21.4".
   - **Any resource pack** `.zip`, such as Faithful or packs from Modrinth and CurseForge.
     HD packs up to 128×128 are used at full resolution; bigger ones are scaled down to 128×128.
     Packs made for versions newer than 1.21 work too. With those, rabbits and magma cubes keep
     Blockcraft's own look, because their newer textures no longer fit the 1.21 models.
3. Click **Done**. The game switches over straight away, even in the middle of a world.

You can stack several packs. The pack at the top of the list wins, and anything it does not
include comes from the next pack down, then from Blockcraft's own art. Use ▲ ▼ to reorder packs,
**Use** / **Turn off** to switch one on or off, and **Default Textures** to go back to the built-in
look. Packs are saved in your browser, so you only add them once. The file is read on your
computer and is never uploaded anywhere, and none of Mojang's assets are included in this repository.
This repository doesn't include any resource packs: Mojang's textures and most popular packs may
not be shared by others, so add them from your own files. If you added a pack before the update
that taught the game the newer file names, add it again once (the screen tells you when): older
versions of the game kept only the files they knew about.

What a pack changes:

- **Blocks and items**, including animated textures (`.mcmeta`), grass, foliage and water tinting,
  block-breaking cracks, chests, beds, signs, banners, the end portal, compass and clock frames,
  paintings, shields and their banner patterns, and armor trims (on the armor and on its icon).
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

## Credits

The biome search tree of Java Edition 1.21 and the reference implementations used to check the
world generator come from [cubiomes](https://github.com/Cubitect/cubiomes) (MIT licence); see
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
