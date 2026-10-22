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

- **Video**: Graphics Fast / Fancy / Fabulous! (leaves, rain distance, the dark screen edges in dark
  places; Fabulous! also shows particles and rain behind water and glass), render and simulation
  distance (mobs move and crops grow only that far), Chunk Builder, Max Framerate, GUI Scale (Auto
  and 1 up to what the window allows), the Attack Indicator under the crosshair or beside the
  hotbar, Clouds Off / Fast / Fancy, Particles All / Decreased / Minimal, Mipmap Levels, round
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

- **All 64 biomes of 1.21.** 53 in the Overworld: plains, sunflower plains, forests, flower and
  birch forests, dark forest, jungles, taigas and old-growth taigas, swamps and mangrove swamps,
  deserts, three kinds of badlands, savannas, meadows, cherry groves, groves, snowy plains, ice
  spikes, snowy slopes, jagged, frozen and stony peaks, windswept hills, mushroom fields, beaches,
  rivers and nine kinds of ocean, plus lush caves, dripstone caves and the deep dark underground.
  The Nether has its five biomes and the End its islands.
- **Java Edition terrain**: new worlds are built by a port of Java Edition 1.21's own world
  generator, so a seed gives the same mountains, rivers, caves and biomes as in Minecraft (see
  below). Worlds run from y −64 to 319, with the deepslate layer, aquifers, copper and iron ore
  veins, and lava lakes, amethyst geodes, dungeons and ores at their vanilla heights.
- **Decoration**: every tree type (including mega jungle and spruce trees, mangroves, azaleas and
  cherry trees), huge mushrooms, coral reefs, kelp forests, bamboo, vines, flowers, sweet berries,
  bee nests, glow lichen, moss and dripleaves in lush caves, dripstone, and sculk in the deep dark.
- **Structures**: villages in five styles with villagers, an iron golem, cats and loot; ancient
  cities in the deep dark; desert pyramids and wells, jungle temples, swamp huts, igloos, pillager
  outposts, ocean monuments, trail ruins, ruined portals, shipwrecks, buried treasure, dungeons,
  mineshafts, trial chambers and strongholds; Nether fortresses and bastion remnants; End cities
  and End ships. Chests are filled from vanilla-style loot tables.
- **Sky and weather**: a day/night cycle with sunrise and sunset, moon phases, stars, 3D clouds,
  fog, rain, snow and thunderstorms with lightning.

### Java Edition terrain from Java seeds

Type a seed on the **Create New World** screen exactly as you would in Minecraft Java Edition
(a number, or any text, which is turned into a number the way Java does it). Blockcraft runs a
JavaScript port of the 1.21 world generator in background workers:

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
  The buildings themselves are Blockcraft's own designs, not Mojang's.

How it was checked: the biomes against [cubiomes](https://github.com/Cubitect/cubiomes) for tens
of thousands of positions on several seeds (Large Biomes too); the terrain splines, default and
amplified, value for value against Java Edition 1.21's worldgen data; the terrain noise, aquifers, surface and carvers
block-for-block against chunks generated by Java Edition 1.21; the spawn point, the structure
starts and the strongholds against cubiomes. Trees, flowers, ores and the other decorations
follow vanilla's rules for each biome (counts, heights, rarities), but are not yet placed
block-for-block like Java Edition, and worlds made before this version keep their old terrain.

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
- **The Warden** rises in the deep dark when sculk shriekers are triggered too often: it sniffs,
  roars, punches and fires sonic booms.
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
  herds (except where a tree stands differently: trees are not yet placed block-for-block).
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
  droppers have Java Edition's quasi-connectivity: power reaching the block above them counts.
- Java Edition timings and quirks: repeaters stretch a short pulse to their delay and lock when a
  powered repeater or comparator points into their side, redstone torches burn out when switched
  off eight times in three seconds, pressure plates stay down for a second (weighted ones half a
  second), and observers see crops grow.
- Hoppers point down or sideways into whatever they were placed against (into a furnace's side
  goes fuel), and pistons break melons, pumpkins, beds, doors, pots and other fragile blocks
  instead of pushing them, so automatic farms built from Java designs work.
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

## Credits

The biome search tree of Java Edition 1.21 and the reference implementations used to check the
world generator come from [cubiomes](https://github.com/Cubitect/cubiomes) (MIT licence); see
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
