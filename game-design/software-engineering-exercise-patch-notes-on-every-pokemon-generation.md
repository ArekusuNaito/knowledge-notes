# Patch Notes on Every Pokemon Generation

This document has an approach of Software Engineering, we are interested on the actual guts of the game. We are not really interested in graphics, music or characters, although you will probably see some comments related to these points as well. Nevertheless, the most important things are actions and rules of the game. Features are game mechanics, they interact with the game state, hence removing and adding features mutates the game state. This document was created as if the games released patch notes of the game, even if it this wasn't as a patches, but you get the idea, documents released like this are pretty much Patch Notes.

I also want to inform people how game-franchises not necessarily improve with newer interations, but at the same time they don't get worse. There's good additions, bad additions,good removals and bad removals.

With this exercise I can only conclude that Pokemon is making more harm than good. The community speaks about the "one step forward, two steps back" and the patch notes yell loudly this point. Players are in their right to worry about the future of this franchise, and any other franchise they care about. Gamefreak is also in their right to change their product as much as they want, because it's their creation, as long as it stays ethical. I can only hope that Game Freak listens to objective fan-feedback and not just try to "[surprise players](https://metro.co.uk/2019/06/18/pokemon-sword-and-shield-hands-on-and-interview-we-try-to-implement-new-things-fairly-gradually-10002483/)" with things they think are a novelty, if you compare this document to other RPGs mechanics you can see that Pokemon has not aged well, the game design is stagnated. There are features that players would love to stay in every-iteration, let's remember how game design aims to create an experience for players, and removing loved features will just ruin players' experiences, and on the other side adding well polished features and quality of life changes makes players have a much greater experience.

I decided to create an age classification of the Pokemon games.

* Golden Age : Generation 1-5
* Silver Age: Generation 6-7
* Bronze Age: Generation 8 \(and probably the next generationsss\)
* Publication date of this document is December 2019, I am covering 23 years of Pokemon mechanics, I understand there are many mechanics that not being covered in-depth \(in-depth coverage has been made from the community\), plus there are mechanics that are missing. Mostly because:
  * My sources didn't have a strong mention to them as well.
  * They were probably over-shadowed by much better features in new games.
  * They were forgettable mechanics.
  * I personally forgot to add them.

Observation: My comments are intended to be objective, as they are biased to game-design/software engineering. Game Design and Software engineering are the core of my previous articles as well. The least objective comments you'll see start with a "Personally I think...", which are things that I like or dislike, and they can also have some objectivity.

I wrote this document all by myself, around 5% of the document was a copy paste, mostly Pokemon lists, or moves. Around 95% was hand-typed by me, you will notice random typos.

#### Special Thanks

Huge thanks to [Serebii](https://www.serebii.net/), [Bulbapedia](https://bulbapedia.bulbagarden.net/wiki/Main_Page) and [Pokemon DB](https://pokemondb.net/) and my family. It is thanks to them I could have a lot of fact checks along with my own Nintendo hardware and Pokemon cartridges.

## Quick Navigation

* [Generation I Mechanics](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#generation-i)
* [Generation II Mechanics](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#generation-ii)
* [Generation III Mechanics](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#generation-iii)
* [Generacion IV Mechanics](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#generation-iv)
* [Generation V Mechanics](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#generation-v)
* [Generation VI Mechanics](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#generation-vi)
* [Generacion VII Mechanics](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#generation-vii)
* [Generacion VIII Mechanics](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#generation-viii)
* [Appendix](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#appendix)
  * [Forms Considerations](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#forms-considerations)
    * [List of Battle Impact Variations](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#variations-that-have-an-impact-in-battle-205-variations-from-136-species)
    * [List of Skin Variations](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#variations-skins-that-dont-have-an-impact-in-battle-257-variations-from-119-species)
  * [Taxonomy of Pokemon Forms](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#classifications-of-pokemon-forms)
    * [Pokemon with Formes](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#pokemon-with-formes)
    * [List of Gender variations](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#gender-difference-forms)
    * [List of Regional variations](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#regional-forms)
    * [List of Mega Evolutions](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#mega-evolutions)
    * [List of Primal Reversion variations](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#primal-reversion)
    * [List of Gigantamax](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#gigantamax-forms)
  * [Attack Dex](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#attack-dex)
  * [Ability Dex](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#ability-dex)
  * [Items Info](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#items-info)

## Mechanics

Let's define what are `Game Mechanics`, leaning more into the software engineering. According to [Sicart](http://gamestudies.org/0802/articles/sicart):

> " Game mechanics are methods invoked by agents, designed for interaction with the game state. "
>
> " The best way of understanding mechanics as methods is to formalize them as verbs, with other syntactical/structural elements, such as rules, having influence on how those verbs act in the game"

* Example: The player uses a Potion.
  * Result: Potions mess with the game-state, as potions interact with Pokemon data, healing, that is, adding HP to the current HP \(that was super fancy to write 🤔\).
* Example: Nidoqueen used Surf in the Overworld.
  * Result: The player can now proceed to water terrain, allowing them to reach new areas of the game, the fact that we can reach new areas is messing with the game-state as well, think of it as an analog of how in other games you can "climb, evade, dash", stuff like that, the big difference is that Pokemon is not an action game and this actions are slower but they change the game-state.

As you can see, when we talk about features, we are talking about interacting with the game and with them, we also talk about mechanics. Removing things like `Condition` or the `Pokeathlon stats` is messing with the state, is messing with the Pokemon data-structures, even if they were removed as interactions in the game, `Pokemon condition` is probably managed internally as a ghost stat because they could potentially add it again, OR/AS remakes were a good example of this.

Another comment is that remakes won't be really be focused for the patch notes, it's probably that many were not added. Remakes features are listed here, but those are features that the overall commmunity consider important. Spin-off games won't be considered here, such as Pokemon Stadiums, Colosseum, XD, Battle Revolution, Let's Go Games. I would love to add a lot of comments from those games but these patch notes will focus on the core-games.

### Generation I

Game Boy ~ 1996

The beginning of our journey.

* Player fight in Battles
  * Turn based combat versus other trainers.
  * Wild random encounters
    * Grass patches
    * "Dungeons" always have wild encounters \(Caves, Power Plant\)
    * Catch Pokemon in these encounters
* Pokedex can
  * Regional and National Dex are the same, since every existent Pokemon are in this Pokedex.
  * Listen to Pokemon cries.
  * Area: This tells you where you can find the selecte Pokemon. A Kanto Map appears.
  * Shows a description of the selected Pokemon
  * Shows Height
  * Shows Weight
  * Total of 151 Pokemon
    * 15 Pokemon Types \(Fire, Electric, etc.\)
    * With 2 versions available you need other games and nintendo systems to complete your PokeDex.
    * Need of multiple games to complete it.
* Pokemon Stats ~ Pokemon interact with...
  * HP
  * Attack
  * Defense
  * Special
  * Speed
  * Individual Values \(Genes\)
* Poke Marts
  * Buy Items
  * Sell Items
  * Different locations have different items. They improve as you progress in your adventure.
* Added PC Storage System
  * Store your caught Pokemon here, since you can only have 6 in your party.
  * Total Boxes: 
    * 12  \(Non-Japan\)
    * 8 \(Japan\)
  * Box Capacity: 
    * 20  \(No-Japan\), 
    * 30 \(Japan\)
  * Total Capacity
    * 240 Pokemon \(All Regions\)
* Items
  * The Bag holds EVERY ITEM. There's no item categories here.
  * You can only hold 20 different items
  * Key Items \[They are not categorized as such here\]
    * Capability of Mapping a Key Item to the Select Button \(Eg. Map bicycle to Select Button\)
    * Town Map
    * Pokeflute
    * Bicycle
    * Keys
    * Rods
  * Pokeballs \(Only useful in Wild Encounters\)
    * 4 Types of Pokeball
      * Only 1 Masterball
  * Usable Items
    * Status Healers
    * HP Healers
    * Evolution Items
    * Stats enhancer
      * Battle Effect Items \(X Items\)
      * Vitamins \(Permanent stat increase\)
    * Moves
      * TMs \(Consumable, limit to 1 use\)
        * One Mart sells TMs
      * HMs \(Infinite uses\)
  * Repel \[Huge and useful mechanic across games\]
  * Escape Rope \(Identical to the Dig Move, but it's consumable\)
  * Mail
* PC Item Storage System
  * The bag has no infinite storage, so you have to store some items in your PC storage system.
  * You can store 50 different items here.
* Item Finder
  * An item that will tell you if there's a secret item on the current map screen. If the ItemFinder makes a sound, means that there's something on your screen, it's very slow. You have to press A in every tile where you walk and see if you can find a "secret" item. These items are not required to beat the game, but they can be helpful.
* Evolution Methods
  * Leveling Up
  * Stones
  * Trading
* Moves
  * 165 Unique moves
  * TMs can only be used ONCE PER PLAYTHROUGH
  * HMs can not be removed.
  * Field Moves \(When selecting a Pokemon, a menu shows up\)
    * Hidden Moves can be used in the overworld to access other places.
    * Dig transport you to a dungeon's entrance
    * Teleport teleports you to the last Pokemon Center
    * Softboiled. Restores up to 50% of the user's maximum HP
* Gyms
  * 8 Gym Leaders to defeat \(bosses\)
  * Gym Badges mark your progress through the game.
    * Obtaining Gym badges allow Pokemon of certain levels to obey the player.
      * Counter mechanic for Pokemon from other games with high levels
    * Obtaining Gym badges also unlock the ability to use Field Moves
* Team Rocket
  * You'll encounter these guys 4 times. There's even 2 dungeons for them.
    * These guys are an actual threat for the current lore standards.
    * Secret Game Corner
    * Silph Co.
* Elite 4
  * Fifth battle to claim the Champion title.
* Safari Zone
  * You can't use any Pokemon here, only bait and stones.
  * The player must pay a fee
  * The player is always given 30 Safari Balls
  * You have only 500 steps in here, this could add pressure to the player for exploration, but at the same time, it will return and explore more \(most likely of the "Fear of missing out".\), players would try to evade areas that were already visited and see if they can find other Pokemon.
  * You get an HM here, the HM will allow you to explore new areas in the game.
* Game Corner
  * Play mini games
    * Get another type of currency to exchange for items or pokemon in these minigames.
* Legendary Pokemon
  * 3 Legendary Birds in 3 dungeons. Optional, but you were rewarded for extra exploration with strong and unique Pokemon.
* Fishing
  * Using different rods you could get Pokemon from different levels.
  * You can attempt fish something in any water tile in the game.
* Happiness Mechanic
  * Only present in Pokemon Yellow
  * Different dialogues depending on Pikachu's happiness value
  * Objectively only useful if the player wants to get a Squirtle
  * The idea is to create a bond with your partner Pikachu. It makes the game look lively.
* Pokemon Daycare
  * Leave a Pokemon here and it will gain experience. Apparently 1 step in the game equals 1 Exp. Point. Pokemon can level up here and even learn moves. You can only leave one Pokemon at the Daycare.
  * Need of extra hardware to do this, the Link cable.
  * You had to go to the Pokemon Center and ask an NPC to access this feature.
* Important Decisions
  * Per playthrough you can only pick one Fossil.
  * Per playthrough you can only pick one fighter \(Hitmonlee or Hitmonchan\)
  * Per playthrough you can only get 1 Eevee \(2 missing for all evolutions\)
* Multiplayer
  * Need of extra hardware to do this, the Link cable.
  * You had to go to the Pokemon Center and ask an NPC to access this feature.
  * PvP battles
    * Players could battle using their Pokemon for "friendly" matches.
  * Pokemon trading
    * This is how you are going to com
    * 1 Pokemon can be traded for another Pokemon's player
* Dungeons ~ Total: 14  \(Caves, Towers, Forests, Hideouts\)
  * I'm not even gonna bother with Routes, the average route is linear, of course there are exceptions. Dungeons are the real exploration in Pokemon games, as those have the real puzzles of the game.
    * Cerulean Cave
    * Diglett's Cave
    * Mt. Moon
    * Pokemon Mansion
    * Pokemon Tower
    * Power Plant
    * Rock Tunnel
    * Rocket Hideout
    * Safari Zone
    * Seafom Islands
    * Silph. Co
    * SS Anne
    * Victory Road
    * Viridian Forest
* Added Pokemon Events
  * These Pokemon are in the game maps as sprites, these Pokemon are not find in the wild, it also makes you wonder what makes them so special, and many players wanted to know more about the lore with them
    * Pokemon List
      * Snorlax
      * As Fossils
        * Omanyte
        * Kabuto
      * Articuno
      * Zapdos
      * Moltres
      * Mewtwo
* Objectives
  * Get 8 Gym Badges
    * Become the Pokemon Champion
  * Defeat the bad guys, Team Rocket
  * Catch all 150 Pokemon \(Since Mew is unobtainable with legit methods\)
* Post game
  * Catch your missing Pokemon
  * Go to Mewtwo's Dungeon and catch him.
  * If during your playthrough you didn't get Articuno, Zapdos and Moltres, this is a good moment to go and explore these 3 dungeons, the most missable is the Power Plant.
  * Some say that it's also good to collect all TMs. Worth mentioning.

[Return to Navigation](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#quick-navigation)

### Generation II

Game Boy Color: 1999

Being the second generation, I will only list new stuff or updated versions of old stuff. If something is removed, I am using the \[REMOVED\] brackets, I can also use the \[EQUIVALENT\] brackets to let you know that even if stuff got removed, there should be an equivalent way to do things.

* \[IMPORTANT\] Game balancing. We will see this stuff in every game. So, while it's considered one "point" here, take into consideration that this point is very very important and time consuming.
* Introducing Day-Night cycle
* Use of Days of the week
* Pokemon can now hold Items
* Pokemon Stats
  * \[IMPORTANT\] Special Stat has been split into
    * Special Attack
    * Special Defense
  * Gender \(Male, Female, Genderless\)
* Pokedex
  * Added 100 New Pokemon
  * Total of 251 Pokemon
  * Connection with Game Boy Printer
  * Pokemon had footprints
  * Option Mode
    * Old Mode - Listed by Evolution Type \(Regional Johto Dex\)
    * New Mode - Listed evolution Type \(National Dex\)
    * Alphabetically A-Z
  * Search Mode
    * Only using Pokemon types
* \[UPDATED\] PC Storage System
  * Total Boxes: 
    * 14  \(Non-Japan\)
    * 9 \(Japan\)
  * Box Capacity: 
    * 20  \(No-Japan\), 
    * 30 \(Japan\)
  * Total Capacity
    * 280 Pokemon \(Non-Japan\)
    * 270 Pokemon \(Japan\)
  * Added Capacity to rename boxes. 
* Items
  * Items now have official categories, separated as "Pockets".
    * Items
    * Balls
    * Key Items
    * TM/HM
  * You still carry a limited number of items, from what I gather, you could still carry from 20-30 items in your Items pocket.
  * Added many items for Pokemon to held
  * Items that increase damage per type
  * Items that when held and trade, will evolve Pokemon
  * Pokeballs
    * Introduced 7 New Pokeballs. Apricorn Pokeballs
      * Craft them at Azalea Town using Apricorns.
      * Different effects that modify the capture rate. \(Eg. Love Ball. Better capture rate if fighting versus a Pokemon of the opposite gender\)
  * Berries are introduced
* \[UPDATED\] Itemfinder
  * Works like the first generation.
  * Now considered a Key Item, meaning that you can use Register the item and do some quick checkings, instead of just opening the bag.
* \[UPDATED\] Pokemon Battles
  * Added 2 new types for a total of 17 types. \(Steel, Dark\)
    * Old Pokemon were reworked to change types due to this. \(Eg. Magnamite is now steel\)
* \[UPDATED\] Pokemon Day care
  * Improved mechanics. You can now leave 2 Pokemon.
  * When leaving 2 Pokemon, these can breed and you can get an egg.
  * Breeding is introduced. By breeding you can get new Pokemon like Pichu, Iglybuff, Clefa, etc.
  * Implemented Egg Groups
* Added Pokemon Forms
  * "Forms" are not a thing until the third generation, but this is the beginning of that.
  * Unown has 26 different forms \(or sprites\). Each letter is a different "form", modern times would call it a "skin".
  * Shiny Pokemon are introduced
    * If in this generation a different sprite is a different "form", then all 251 Pokemon  have a "shiny form".
    * Only certain Unonwn letters can be shiny due to how the game manages shinyness. IVs are linked to Shinyness.
    * Probability to find a shiny: 1/8192
* Added Breeding \(pretty complex already, in terms of deep mechanicss\)
  * Moves are passed to new generations.
  * Father is the one in charge of passing moves.
  * Mother determines species
* \[REMOVED\] Safari Zone
  * \[EQUIVALENT\] Bug-Catching Contest
    * Can only enter Tuesdays, Thursdays, Saturdays
    * Overall, Safari Zone has more to offer than the Contest
* Added Move Deleter
  * In the first game, you could not remove a Hidden Move. The philosophy behind this was that players could get stuck in an area if they got rid of a Pokemon with a Hidden Move.
  * This is an NPC that will delete any move you want, even Hidden Moves.
* \[UPDATED\] Happiness
  * The happiness system is enhanced. Now it's not a thing of just Pikachu.
  * Every Pokemon has a happiness value.
  * Some Pokemon evolve if they are happy.
  * Moves like Return and Frustration use this Happiness value
* Added New Evolution Methods
  * Added happiness
  * At certain time of the day
  * By trading AND holding an item at the same time.
* Team Rocket
  * Smaller threat due to disbandment in the previous game.
  * You'll have 4 different encounters. Overall, same or slightly better than the previous game. Worth noting that you help the Champion, Lance.
    * Slowpoke Well
    * Rocket Hideout
    * Radio Tower at Goldenrod city \(Cool boss battles with Executives\)
    * Cerulean City
  * The last encounter is just a Grunt hiding a machine part.
* Objectives
  * Get 8 Gym Johto Badges
  * Defeat Team Rocket
  * Defeat the Elite 4 \(Which is Kanto's Elite 4 with new members\)
  * Get 8 Kanto Badges
  * Catch 251 Pokemon
  * Defeat Red, the protagonist of the first game
* Post Game
  * You could say that Kanto is the real post-game. When you defeat the Elite 4, you get to see the credits. Aim for those new 8 gym badges.
  * Catch the missing Pokemon to complete your Pokedex.
  * Defeat Red
* Added Pokegear \(2nd Generation Gadget\)
  * Gen II introduces a helper gadget with small helpful "apps" that improve the Quality of Life of the games.
  * It has a clock and calendar.
  * There's no more "Town Map" Item, the Pokegear has this included
  * Phone
    * Call other NPCs to get rematches \[INTRODUCING TRAINER REMATCH\]
    * Introducing Swarms. NPCs can call you as well. There are trainers who tell you when a "rare" Pokemon has appeared, they even tell you which location to go. 
      * The Swarm lasts 30 real time minutes.
    * Prof. Elm gives you storyline stuff
  * Radio
    * Use the slider to tune different radio stations. 
      * Some discuss or inform about "lore" of the game.
      * Tune to listen to locations of some pokemon.
      * Tune to listen to music, like a real radio!
      * Tune to listen to your Lucky Number, if you entered the Lucky Number show. You can get a prize
      * \[Interesting game feel\] 
        * Lorewise, The evolution transmission was used to force magikarp to evolve, Team Rocket created this transmission, and this is the reason of why the Red Gyarados exists. 
        * [Serebii](https://www.serebii.net/crystal/pokegear.shtml) lists that the Evolution tranmissions's effect is to force Magikarp to evolve. I tried to do this myself and it doesn't seem to be true, I caught a Magikarp, tuned in the tranmission, I even leveled up a Magikarp to level 11 with the tuned transmission and it never happened, my magikarp NEVER evolved using the transmission.
        * The magikarp forcing evolution had potential as a mechanic during that part of the game \(and future Pokemon games could as well potentially base other evolution methods in this creepy things\). Evolving a low level magikarp is not harmful game-design wise, as even if you bring a low level Magikarp, you would get a low level Gyarados, which will probably be useless because of the same thing, plus trainers have stronger Pokemon than level 20. Plus there are many Pokemon in-game that they should not even exists, you probably have seen a Lv.7 Pidgeotto in older games.
        * The fact that you can use  the radio and tune in the evolution transmission is a good detail, but it would probably be something weird and even a morale dilemma tu use it, which would be a reason to scrap them for "a kids game".
      * \[Interesting game feel\] At the Ruins of Alph you can tune this station to listen to a creepy thing, but it helps with the game immersion. They seem to be the Unown cries.
      * In Kanto, tune in a station to Increase Wild Encounters
      * In Kanto, tune in a station to Decrease Wild Encounters
    * As a game system, this is what the radio allows you to do \(using the info from the previous point\)
      * Lucky Number. Chance to Win an Item
      * Decision to change your game music
      * Obtain Pokemon locations
      * Increase Wild encounter rate \(Only certain days\)
      * Decrease Wild encounter rate \(Only certain days\) \(Like a kind of Repel Item\)
      * Use a radio station to Awaken your Pokemon \[Equivalent of Pokeflute in Gen 1\]
* Your Room \(Personal Customization\)
  * Feature to allow the player to add a personal touch to the room. Minimal customization, but during this era it kinda felt like a big thing. Nevertheless, being the first iteration it was a huge success, it even had a connection with Pokemon Stadium 2.
  * Decorations
    * Bed
    * Carpet
    * Plants
    * Poster
    * Video Game Console
    * Dolls
    * Trophies
* \[UPDATED\] Pokemon Events
  * Lapras
  * Sudowoodo
  * Red Gyarados \[SHINY!!\]
  * Voltorb
  * Electrode
  * Snorlax
  * The Beast Trio roams in Johto
  * Suicine \[CRYSTAL ONLY\]
    * In this version it will go back to Tin Tower as an interactable Pokemon
  * Lugia
  * Ho-Oh
  * Celebi \[EVENT EXCLUSIVE\]
    * The first event exclusive Pokemon using the Mysterious GS Ball
* Added The Battle Tower \[CRYSTAL VERSION ONLY\]
  * This is the first time the series introduces a more "balanced" battle challenge. In any game, you could be fighting weaker or stronger pokemon than the ones you have. You could start the game with  a Level 100 Celebi and beat the game with that Celebi, while the Pokemon in the story are from level 5 to level 50. The facility idea probably came from the `N64 Stadium` games, where the player participated in different cups with different rules that were more balanced than a normal playthrough. 
  * Added 10 Challenges in different 10 Floors. Defeat the trainers in each floor.
  * Each floor's rule is to use Pokemon of certain level. 
    * 7 Battles in a row per floor
    * At Floor 1 you can only battle with Pokemon of Level 10 an so on
    * At Floor 10 you can only battle with Pokemon of Level 100
  * You can't use 2 Pokemon of the same species \(no 2 or 3 charizards on the same team\)
  * You can't use the same held item. \(Eg. You can't have all 3 holding Leftovers\)
  * You can't use Legendary "non-trio" Pokemon. \(Mew, Mewtwo, Ho-oh, Lugia, Celebi\)
  * Your reward is self-acomplishment, plus Vitamins.
* Added Move Tutor \[CRYSTAL VERSION ONLY\]
  * This NPC teaches certain moves to Pokemon. In this generation they cost Game Corner coins.
  * As long as you pay for coins, you can teach moves.
* Added Mystery Gift
  * Used to receive items from other games, like Pokemon Stadium 2.
  * You could get furniture for your Room.
* Dungeons ~ Total: 21   \(Caves, Towers, Forests, Hideouts\)
  * Johto
    * Sprout Tower
    * Ruins of Alph
    * Union Cave
    * Slowpoke Well
    * Ilex Forest
    * Bell Tower
    * Glitter Lighthouse
    * Whirl Islands
    * Mt. Motar
    * Rocket Hideout
    * Goldenrod Radio Tower
    * Ice Path
    * Dragon's Den
    * Dark Cave
    * Tohjo Falls \(Connecting both regions\)
  * Kanto \(Many of them are not very dungeon-like, just one big room\)
    * Victory Road
    * Diglett's Cave \(Very linear\)
    * Mt. Moon \(Only one Floor\)
    * Power Plant \(Only one floor\)
    * Rock Tunnel
    * Mt. Silver
* \[IMPORTANT\] Added the capacity to trade Pokemon between both generations. 
  * The first 151 are 2-way tradeable, while the new 100 can only be traded between the second generation games \(which is expected\).
  * This was called the Time Capsule

[Return to Navigation](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#quick-navigation)

### Generation III

Game Boy Advance: 2002

We are gonna talk here about Ruby, Sapphire and Emerald. The remakes will not be considered. Remakes should be improving the previous stated points from the generation been remade. As stated before, if it appears to be missing points, it's because it's something that was introduced in a previous generation and it wasn't removed in this generation, having retroactivity, also many things could slip my document, there's a lot of points here and it really took a while to write this down.

* Added Weather in the Overworld
  * Rain
  * Intense sun
  * Sandstorm
* \[UPDATED\] Pokedex
  * 135 New Pokemon
  * Total of 386 Pokemon
  * Regional Mode lists 202 Pokemon.
  * Option to go to the top of the Pokedex \(Treecko\)
  * Option to go to the bottom \(Last one the player has seen\)
  * When selecting a Pokemon you can see the Size comparison versus the Player Character
  * \[UPDATED\] Search Mode
    * Order Option \(You could do easy sorting using SQL in modern days\)
      * Order By Pokedex Number
      * Order Alphabetically
      * Order By Weight \(Which is essentially descending or ascending\)
        * Heaviest 
        * Lightest
      * Order By Height
        * Tallest
        * Smallest
    * Search by letter, but from 3 to 3 letters \(ABC,DEF,etc\)
      * Results are ordered with the selected "Order Option" explained in the last point.
    * Search by color \(Seems like part of the new Pokemon data is what color the Pokemon is\)
      * Red, Blue, Yellow, Green, Black, Brown, Purple, Gray, White, Pink
  * Shift Option
    * Choose which is the default Pokedex listing. This uses the Order Option from Search mode.
      * Numerical
      * Alphabetically
      * Using Weight
      * Using Height
    * National Dex
      * This option must be unlocked. To upgrade the Pokedex, the player must trade Pokemon with first generation remakes. Makes sense, since it's a Pokemon that doesn't appear in the region.
  * \[REMOVED\] Capacity of trading Pokemon with previous generations.
    * So how can you get all 386 Pokemon? Due to technical limitations with how the internal Pokemon data is handled this was removed, you CAN'T trade your Pokemon from generations 1 and 2. 
    * They created Generation I remakes so you could get all 386 Pokemon in any generation 3 game. A step back, but it's something they took care of.
* \[UPDATED\] Pokemon Stats
  * \[REWORKED\] IVs
  * Added the EVs: Effort Values
  * Added 25 Natures
  * Added Abilities
    * Added Outside of Battle Secondary effects when in your party. \[EMERALD ONLY\]
      * Some abilities have effects when you are in the Overworld. Eg. Magma Armor makes eggs hatch faster.
      * Some abilities require Pokemon in the first Party slot.
      * This continues in the next generations.
  * Added Condition \(Coolness, Beauty, Cuteness, Cleverness, and Toughness\)
  * Added Ribbons
    * Considered Achievements per Pokemon. Examples:
      * When winning contests
      * When got all Effort values
      * For winning at the Elite 4
      * For winning 100 trainers in a row at the Battle Tower
  * Game tracks which Pokeball you used to catch a Pokemon
* Added Move Reminder
  * A very useful character. If you've ever had a Pokemon that evolved past their evolution level, chances are that a move that learns when it evolved was something your pokemon didn't learn. This character can teach your Pokemon moves that they were able to learn from previous levels.
  * This comes with a price, you have to pay him a `Heart Scale`.
* \[UPDATED\] Pokemon Battles
  * Introducing Double battles, fight 2v2!
    * Introducing Multi-battles! Essentially a double battle, but you can only control one Pokemon. Your ally Pokemon is controlled by another player. The 2 enemy pokemon are controlled by 2 opposing trainers. 4 Trainers, 4 Pokemon.
* \[UPDATED\] New Pokemon Forms
  * This generation introduces "real" Pokemon forms. 
    * Castform has 4 forms.
      * every form has a different type \(which has an impact on pokemon battles\), unlike Unown which is just another "sprite. But still, remember that those sprites had to be designed and added to the game.
    * Deoxys changes form depending on the version he is in.
      * 4 Forms
* \[REMOVED\] Your Room
  * \[EQUIVALENT\] Secret Bases
    * Overall, an improvement of "Your Room" from gen 2.
* \[UPDATED\] Items
  * \[UPDATED\] Categories are like this now
    * Items
    * Pokeballs
    * TM/HM
    * \[NEW\] Berries
    * Key Items
  * Pokeballs
    * \[REMOVED\] Apricorn Balls \(7 Balls\)
    * Added 7 New Balls
      * Dive Ball
      * Luxury Ball
      * Nest Ball
      * Net Ball
      * Premier Ball
      * Repeat Ball
      * Timer Ball
* \[UPDATED\] PC Storage System
  * Added the capacity of changing the wallpaper
  * Total Boxes: 14
  * Box Capacity: 30
  * Total Capacity: 420
* Mirage Island \(Random Event to encounter this misterious island\)
  * While in modern times this might be silly. Back in the day when not everyone had internet, this was something people talked about.
* \[UPDATED\] Battle Tower
  * Your pokemon are NOT auto-leveled, you must have Level 50 or Level 100 pokemon, this can be time consuming.
  * \[REMOVED\] No more 10 Floors, 10 Challenges.
  * \[UPDATED\] 2 Formats now. Pokemon in Level 50 or Level 100.
  * Singles Mode \(3v3\)
  * Overall this facility has been upgraded, even if there's no more different level challenges.
* Battle Frontier \(Emerald Only\)
  * Exclusive to Pokemon Emerald, this is a huge post-game location. Imagine having features from a Pokemon Stadium game in a core series game, many facilities are here in this location. Rather than just having the Battle Tower like in Ruby and Sapphire, the Battle Frontier has a lot of facilities with different rules.
  * The Objective is to defeat the Frontier brains, which are way harder than the story mode. Every facility features a Frontier Brain. You have to beat the facilities many times in order to have chance to challenge the frontier brains.
  * Added the IV Judge NPC.
    * This character tells you how good your Pokemon Genes are \(IVs\). But this NPC will use a spoken language, it will not be anything numerical. Here's an example for perfect IVs
      * `It's flawless! A thing of perfection! ...Hmm... That's how I call it."`
  * Trainer Card is now upgraded as the Frontier Pass. Aside from badges the player can also obtain the Frontier Symbols.
    * \[IMPORTANT\] You could record one battle in your frontier pass so you can watch it later and even have some bragging rights to your friends. While it was a limited feature, specially within a GBA Cartridge, it meant a lot to know that in this era we had battle replays.
  * \[UPDATED\] Battle Tower 
    * In Emerald, the Battle Tower is one of many buildings at the Battle Frontier.
    * Level 100 format is now "Open Level" 
    * The frontier brain can only appear in Single Battle Mode
    * New Battle Modes 
      * Doubles Mode \(4v4\)
      * Multi Mode with a friend \(2,2 vs 2,2\)
  * Battle Pike
    * Challenge of defeating 7 rooms.
    * Every time the player wants to advance, they are given a choice of which room they want to go.
    * Your pokemon won't get healed after any room, there are rooms that will heal you.
  * Battle Dome
    * A tournamente between 16 trainers.
    * Players can view the info about the other trainers.
  * Battle Factory
    * Use of rental Pokemon
    * You can switch Pokemon with trainers you defeated
  * Battle Arena
    * A similar format like in the battle tower.
    * It's a 3v3
    * You can't switch Pokemon
    * You have 3 turns to defeat a Pokemon
    * After 3 turns, you will be judged by the referee, the pokemon who loses, faints.
  * Battle Palace
    * An Autobattler, Pokemon fight on their own. This is dependant of the Pokemon's nature.
  * Battle Pyramid
    * A Challenge Dungeon per floors. 
    * You can navigate the pyramid
    * Start with no items, but you will find items along your way.
    * Floors are dark, but you get more vision along your way.
    * Field moves like Soft-boiled are useful in this facility!
* Collect Soot to acquire special items.
* \[UPDATED\] Move Tutor \(Emerald Only\)
  * Why is this feature only present in Emerald and Skipped in Ruby and Sapphire?
  * Like Pokemon crystal, you can teach moves as many times as you want. The downside is that they cost battle points, and they are only obtainable by winning at the facilities.
* \[UPDATED\] Swarms
  * Instead of using phone as in generation 2. The player must watch a TV Show. Then becomes active.
  * No Longer last 30 minutes. They last a whole day.
* Added Berry harvesting
  * You can find berries at harvest them.
  * You can plant berries on soil. This makes berries a renewable resource, potentially infinite overtime.
* Added Pokemon Contests
  * Every condition has 4 levels. Players are invited to conquer all conditions in Master Rank
  * Mini game that features 4 participants and a Judge. Only one Pokemon will be consider the "Coolest" or the most "Beautiful". 
  * Multiplayer was possible.
  * Added PokeBlocks. These are used to raise Pokemon's condition.
    * Create Pokeblocks with the Berry Blender.
    * Berry blending can be multiplayer.
  * \[IMPORTANT\] Remember that there are `354 Moves` in this game? Well, the team had to take their time to add them a move conditio and effect in thiss game. When you play the game it doesn't feel like much, but it's still development time and effort. Consider this as one reason to add or remove the contests in future games.
* \[UPDATED\] Generation Gadget \[PokeNav\]
  * No more PokeGear from Gen 2.
  * \[REMOVED\] Radio
  * Added condition check. 
    * Check for Pokemon with certain "condition" stats. These are the Pokemon Contests useful stats.
  * \[UPDATED\] Trainer Rematches. The Trainer Eyes allow you to rematch some trainers in  the game.
    * First time ever. Gym Leader Rematches \(Emerald Only\)
      * Double Battles
      * Sadly you can't get a rematch anytime you  want
* \[REMOVED\] Bug-Catching Contest
  * \[REWORKED\] Safari Zone
    * You can use Pokeblocks to attrack Pokemon, instead of bait like in generation 1.
* Added Record Mixing
  * Need to go to a building called Record Corner
  * Television Shows will feature the players you mixed records with
  * Other players secret bases will be in your game, including the whole layout they have in their games.
  * The Mauville Pokemon Center Men. Curious NPCs that are generated with your trainer ID.
    * One of those NPCs is the Story Teller. Tells you records from your or other players.
  * Pokemon Trainer Fan Club. Praise recorded players for their achievements. Similar to the Mauville Men.
  * Feebas Factor.  Feebas is hard to find, as it only appears in specific water tiles in your game. When mixing records, tiles will change to the recorded player's.
  * Battle tower records
    * Player who mixed records can appear as recorded trainers at the battle towers, with the same team and moves.
  * Eon Ticket. Consider it a viral item. If someone has the Eon Ticket, it can be transmited to other players so they can catch Latios or Latias.
  * Mix records at the Record Hall \(Emerald Only\)
  * Mix Swarms from other games to get exclusive Pokemon during the swarm duration.
* The Trick House. A small 8 puzzle dungeon. You get new dungeons as you progress in the game.
* Team Magma / Team Aqua
  * Each version has a different team. Which is a way, it's a "good" reason to have 2 versions of the same game. The game features a better narrative and it's the first time the story is relevant to the game, instead of just "just go catch stuff and become the champion".
  * There are 8 encounters, even more than the previous generation.
  * From Serebii. "Depending on the version. They either want to use Groudon to expand the land masses to give more room for land Pokemon, or use Kyogre to expand the oceans to give more room for sea Pokemon. In both cases the opposite team serves a supporting role to you in the story."
* \[WORSE\] Your Rival 
  * This is the first time you get a friendly rival. Sadly this generation has a very weak rival. You don't even get to see the final evolution of their starting pokemon. Blue and Silver are better rivals.
  * At the same time, you get a second rival, Wally.
    * Wally becomes stronger than your first Rival.
* Added Two kinds of Bicycle
  * Mach Bike
    * Faster Bike
  * Acro Bike
    * You can perfom tricks
  * You can't have both bikes at the same time. From a design perspective, this just could be solved when by merging them at the end of the game, as a "reward". 
  * Both Bikes allowed you to proceed to different terrains.
* Added Stats/IV Judge \(Emerald Only\)
  * This NPC will tell you in a "spoken language" if your Pokemon has good genes \(IVs\).
* Dungeons. Total: 23 \(or 30 with Trick House\)
  * Abandoned Ship
  * Aqua/Magma Hideout
  * Artisan Cave
  * Cave of Origin
  * Dessert Underpass
  * Faraway Island
  * Fiery Path
  * Granite Cave
  * Magma/Aqua Hideout
  * Marine Cave
  * Meteor Falls
  * Mt. Pyre
  * Navel Rock
  * Petalburg Woods
  * Seafloor Cavern
  * Sealed Chamber
  * Shoal Cave \(It even changes depending of the time of the day\)
  * Sky Pillar
  * Southern Island
  * S.S Tidal
  * Terra Cave
  * Victory Road
  * Trick House \(Many puzzles!\)
    * 8 Chambers. We can say it's one big dungeon, or 8 mini dungeons.
* \[UPDATED\] Pokemon Events
  * Like previous games, there are Pokemon you find in the Overworld and they add a layer of exploration and lore that makes players wonder why you find these pokemon this way.
    * Pokemon List
      * Kecleon
      * Rayquaza
      * Regirock
      * Regice
      * Registeel
      * Latias
        * Roams in Sapphire
        * Interactable in Ruby with the Eon Ticket Mystery Gift \(This is very exclusivity beecomes more annoying\)
      * Latios
        * Roams in Ruby
        * Interactable in Saphhire with the Eon Ticket Mystery Gift
      * Groudon \[RUBY ONLY\]
      * Kyogre \[SAPPHIRE ONLY\]
      * Rayquaza
      * Sudowoodo \[EMERALD ONLY\]
      * Mew \[EVENT EXCLUSIVE MYSTERY GIFT\]
* \[UPDATED\] Breeeding
  * This feature has been enhanced too, sadly, breeding it more technical than the average points listed here, for the sake of "layman terms", not much details will be covered, as the "philosophy" behind this too is the fact that "every pokemon is unique" and there has to be "hidden" infomation, to keep stuff like genes "special". Breeding small details could be a huge section, but we are talking about many mechanics, not just breeding, be aware that many things might just touch the surface but are even more complex inside.
  * Baby inherits 3 IVs from parents.
  * Using items, like the everstone can make a pokemon to inherit the parent's nature. 
* Post Game
  * Complete your Pokedex
  * Catch the in-game legendaries
    * 6 legendaries in one save file
  * Win all Master Rank contests
  * Complete the Trick House challenges
  * Defeat 50 trainer challenge in Battle tower
* \[UPDATED\] Trainer Card
  * This is the first time the trainer card is _relevant_. While it appeared in the previous generation, you can get stars for completing specific tasks. Every post-game activity I listed, except for the trick house.

[Return to Navigation](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#quick-navigation)

### Generation IV

Nintendo DS: 2006

The games are Diamond, Pearl and Platinum. Let's list more mechanics. There's a lot of things that improved by having 2 screens.

* Added Transfering Pokemon from Other generations
  * You can transfer Pokemon from the III to the IV generation by going to a place called the "Pal Park".
  * \[REMOVED\] Two-way generation transfer
  * You can only transfer one way, from third to fourth.
  * At this facility you catch the Pokemon using Park Balls
  * You transfer a max of 6 Pokemon everytime you go to the Pal Park
* \[UPDATED\] PC Storage System
  * Total Boxes: 18
  * Total Capacity: 540
* Added Amity Square
  * 11 Pokemon from 493 can follow you at the Amity Square.
  * A special area to make Pokemon find accesories and berries
* Added Any Pokemon following you \[HEARTGOLD/SOULSILVER ONLY\] 
  * While this is a remake feature, it is a feature that pretty much everyone loves, considering that you can see your partner pokemon, remember that the Pokemon games and even the anime convey the players to create a bond with pokemon, and while this is a "useless feature" because it's just an NPC thing following you, it's something that everyone loves!
  * A feature that returns from Pokemon Yellow, this time ANY POKEMON can follow you. As long as it's the first on your party. 
  * Yes. Any Pokemon, all 493 Pokemon with their different forms and even gender differences, meaning that they had to do more than 493 sprites for every cardinal point.
  * If your pokemon is shiny it even displays as a shiny
  * Consider that this is a lot of graphical work, it's a lot of sprites.
* \[UPDATED\] Mystery Gift
  * You can now receive gifts from the Internet
  * Get wireless with the included DS Wireless communications, instead of extra hardware like in the third generation.
  * Share with friends using the "Get from friend"
  * Some gifts allow you to trigger special events in game. Like the Darkrai Event
* Added Pokeball Seals
  * A very interesting feature that was exclusive to this Fourth generation.
  * Add seals to customize how a Pokeball will have its release animaton.
  * 13 seals to customize ANY Pokeball
* \[UPDATED\] Move tutors 
  * No longer a thing from "Special versions".
    * Whoops! Did I say special versions? Yeah! While Diamond and Pearl HAVE move tutors, they only teach 4 moves... if you want more moves you have to get Platinum, once again,  A STEP BACK AND A STEP FORWARD, this is such a bad decision to make that is only supported because of business.
  * Platinum and Remakes
    * They have more move tutors with A LOT of moves to teach to Pokemon. Could you call this Pay 2 Win?
* \[UPDATED\] Day-Night Cycle. While it wasn't completely "missed" in generation 3. It's not something you can really see in gen3, there's no feedback of time, it's always daytime, but there are still time mechanics. In this game, you can see how time passes as the areas look different depending of the time.
  * Like in second generation, there are songs that that show up at day or nighttime.
* Pokedex
  * 107 New Pokemon
  * Regional Mode lists
    * 151 Pokemon in Diamond/Pearl
    * 201 Pokemon in Platinum
  * You can see Pokemon entries in other languages if you get a Pokemon from that region.
  * Fully functional Touch Pokedex. Great stuff here
  * \[UPDATED\] You can compare the height of the Pokemon with the player. It even tells you how tall you are.
  * Added Weight comparison, there's even an animated scales.
  * You can unlock the National Mode by SEEING all Pokemon in the regional mode and you have to beat the Elite four.
  * Removed `Shift Option`, your default Pokedex listing can only be Regional or National.
  * \[UPDATED\] Search Mode
    * The same core functionality than Generation 3 but you can add more search filters. Generation 3 only had 1 filter per search, you can combine them here.
    * For example, you can search pokemon ordered by Height \(Tallest/Smallest\), only Pokemon with letters PQR, and search with any type you want, like Electric \(or if you want a second type, you can add it too\) 
    * New Filter: Search by "Form", which the Pokedex names as "Body Style". 
    * It's a small improvent in terms of functionality, but the UI is more intuitive thanks to the second touch screen.
  * Since the Day-Night cycle is back, when you look a Pokemon's area, you can use the touch screen to change the time of the day. And you can see if a Pokemon can appear at a certain time.
    * Morning
    * Day
    * Night
* Items
  * \[BIG UPDATE\] The bag has now infinite space
    * PC ITEM Storage system is obsolete.
  * \[UPDATED\] Item Pockets are updated once again, for good.
    * Items
    * Medicine
    * Pokeballs
      * Added Dusk Ball
      * Added Heal Ball
      * Added Quick Ball
      * \[UNOBTAINABLE\] Added Cherish Ball 
        * You can only get Pokemon that already have this Pokeball, this ball is for event Pokemon
      * Added Park Ball.
        * Used to catch the Pokemon from third generation.
    * TM/HM
      * Older generations had 50 TMs, there are now 92 TMs, almost double the moves.
    * Berries
    * Mail
    * Battle Items
    * Key Items
* \[UPDATED\] Berries
  * Added 21 Berries
  * Total of 64 berries
  * Berry Pots \[HEARTGOLD/SOULSILVER ONLY\]    
    * As mentioned before, while we don't really talk about remakes, there are some features that are an improvement to the franchise.
    * There is no soil in the Johto remakes. So you can carry Berry pots, which is a key item.
    * Why is this relevant? Because there's no need to go and check your berries at certain routes. YOU CAN CHECK YOUR POTS AT ANY TIME. That's a feature that is relevant, it can be time consuming to go and check all berries.
* \[UPDATED\] Moves
  * \[BIG UPDATE\] ALL MOVES had to be reworked \(yes, all of them had to have a review\). 
    * From Generation 1-3, move's stats were linked to the Type, Fire Type moves were always special attacks, this is, if you hit with Fire Punch which is essentially a move that is using Physical strength, but it was considered a Special Move because Fire Type moves were always Special. 
  * There's a total of 467 Moves in this generation.
* Games can now connect to Internet!
  * Use of DS friend-codes to connect with other players
  * Enjoy the old features you had in local play but you can do them over the internet now. Trade and battle with your friends online.
  * For Free, no subscription or anything.
  * Use voice chat to talk with your friends, possible with the built-in DS Mic.
  * Global Trade Station ~ GTS
    * Added theAllows to look for a Pokemon you want and trade it for something in return. Players will deposit pokemon here expecting a trade.
    * The Geonet can be used to set your real world region, because GPS is not something we had during this era in games.
    * \[UPDATED\] GTS is now known as the "Global Terminal", the building has more features. \[PLATINUM AND HEARTGOLD AND SOULSILVER ONLY\]
      * You can view other player's PC Boxes.
      * You can view `Super Contests Dress up` pictures
    * The Vs. Recorder is now a separeted feature and key item from the Frontier Pass that was introduced in the previous generation. \(As a note again, why was this feature not in Diamond and Pearl?\)
      * The videos are called "Battle Videos".
      * You can record from
        * The battle frontier
        * Wireless Battles \(Local\)
        * Wi-Fi Battles \(Online\)
    * Watch your videos
    * Players can upload videos to the Global Terminal
    * Players can download videos from the Global Terminal
* \[UPDATE/IMPORTANT\] New Pokemon Forms
  * Some Pokemon now have gender differences. Which will be counted to  "skins", like Unown. 
    * Kanto: 22 Pokemon have new gender differences
      * Remember that Nidoran 🚹 and Nidoran 🚺 were the first pokemon with a notorius difference?
    * Johto: 22 Pokemon have new gender differences
    * Hoenn: 18 Pokemon have new gender differences
    * Sinnoh: 31 Pokemon have new gender differences. This makes me think that gender differences were put into consideration when creating the designs of this new pokemon, there are more pokemon with differences in Sinnoh than other differences.
    * Total: 93 Pokemon have gender differences \(94 with Nidorans\). Remember that this has to be taken into consideration with stuff that has to be carried over to new generations. We are not just talking about 493 Pokemon now, we are talking about 493 plus 96 gender differences,plus other forms, plus shinies, while it's not double the workload, time will be used to support of all this different Pokemon variations, right now we are not dealing with 493 pokemon designs, we are dealing with more.
* Dungeons ~ Total: 15 \(Although there are other, non-dungeon areas that are great for exploring with the new HMs\)
  * Distortion World \(Linear\)
  * Eterna Forest
  * Eterna City Team Galactic Building \(Improved in Platinum\)
  * Fuego Ironworks
  * Grand Marsh \(Sinnoh's Safari Zone\)
  * Lost Tower
  * Mt. Coronet
  * Old Chateau
  * Ravaged Path
  * Snowpoint Temple
  * Solaceon Ruins
  * Stark Mountain
  * Team Galactic HQ
  * Turnback Cave
  * Victory Road
  * Wayward Cave
* \[UPDATED\] Generation Gadget \(Poketch\)
  * The new gadget is called the Poketch. It has 22 "in-game apps", and you could get up to 25 apps with Nintendo events.
  * \[REMOVED\] "Detailed" Town Map is back to be a Key Item.
    * But you can have a less detailed version of your map in your Poketch.
  * \[REMOVED\] Condition Check
  * \[REMOVED\] Trainer's Eyes
  * Apps
    * Digital Clock
    * Calculator
    * MemoPad. You can use your stylus to do handwriting notes
    * Step Counter. Literally counts every step you take
    * Your Party. You can see the 6 Pokemon at your party. Just a quick way to look t the party, instead of going to the menu.
    * Happiness Checker. Happiness has been since generation 2. Hold the touch screen where your Pokemon is to see its happiness, from 2 hearts and onward, the Pokemon can evolve.
    * \[UPDATED\] Itemfinder. A different approach to use the ItemFinder, this one is very quick, as for one tap to the screen it will tell you if there's something secret along the way in a matrix screen. The best Itemfinder until now
    * \[NICE IMPROVEMENT\] Berry Checker. You can see at the screen which area has mature berries to be harvested. No need to go and check personally.
    * Day-care checker
      * You can see the Pokemon you left there
      * Current Levels
      * Your Pokemon genders
      * It will show if an Egg was produced
      * It is a good feature, it is something that we lost in other generations, but it's something not relevant, considering that when people goes to the day-care, spends a lot of time there. But it was nice to just keep walking and just update the screen and see if there was an egg or not. THERE WAS NO NEED TO TALK TO THE NPC.
    * Pokemon History
      * Just displays the most recent 12 pokemon you got. Either:
      * Captured
      * Evolved
      * Hatched
      * Traded
    * Counter. An in-game counter that you can use to count anything you want.
      * Resets when changing to another app or turns off the game.
    * Analog Watch. Yeah, just a watch, because the poketch is a watch.
    * Marking Map
      * Displays a basic map of Sinnoh.
      * You can drag markings to place at certain spots. Useful for anything you would like to remember or "mark".
      * You can see the roaming pokemon for the game.
        * Cresselia
        * Mesprit
        * Legendary Birds \[PLATINUM ONLY\]
    * Link Searcher
      * Lists number of games particpating in Wireless communications.
        * Union Room
        * Underground
        * Colosseum
      * Moving causes communication to end
    * Coin Toss. Literally just that
    * Move Tester
      * If you want to experiment type effectiveness, you can use this.
      * Pick a type for your move and 2 types for the enemy pokemon. The app will tell you how effective your move will be.
    * Calendar. Shows the day of your Nintendo DS system
    * Dot Artist
      * A matrix to draw.
      * You can create pixel art here
      * It has different pixel shades. 4 to be exact.
      * The image is retained even if you leave the app or turn off the system
    * Roulette
      * You can draw on the roulette.
      * Push the play button to spin the roulette
      * The idea is that, since you there are drawings on the roulette, you can do something random with the drawings. This is up to the player's imagination
    * Trainer Counter
      * Lists the top three pokemon you encountered using the Poke Radar
      * The top area will display the current chain for shiny hunting
    * Kitchen Timer
      * A timer that has an alarm when it reaches 0.
    * Color changer. Yeah, just that, change your Poketch color
      * 8 colors
    * Matchup checker \[EVENT ONLY for Diamond and Pearl\]
      * It checks for breeding compatibility.
    * Stopwatch \[Never distributed\]
      * Just a time counter.
    * Alarm Clock \[Never distributed\]
      * Rings an alarm given a certain time of the day.
* Added Union Room
  * Although it was introduced in FireRed and Leaf Green and then it was introduced in Emerald, these special versions are not considered for the actual normal versions of the game.
  * \[REMOVED\] The need of extra hardware like the Link Cable. Trades and battles can now be done with Wireless communications
* \[UPDATED\] New Evolution Methods
  * Gender based evolutions
  * Hold an specific item and then level up at a certain time of the day
  * Area evolution.
  * Attack based evolutions and level up. Just by knowing the attack the pokemon will evolve
  * Having another Pokemon in the party
* \[UPDATED\] Super Pokemon Contests
  * A player's goal could be to collect all accesories for the contests
  * Visual Competition
    * Condition Section
    * Dress-Up Section
      * You have to get Accesory prizes
  * Dance Competition
    * Mimic rhythm Mini-game. Contestants must mimic the other Pokemon steps.
  * Acting Competition
    * An Upgrade of the second round for generation games where you have to use moves for the judges
* \[REMOVED\] Pokeblocks
  * Added Poke poffins
    * This is the equivalent of Pokeblocks for the 4th generation.
* Added the Poke Radar
  * A key item used to find wild Pokemon in grass.
  * There are Pokemon that only appear with this device, around ~44 Pokemon.
  * It is used for Shiny Hunting, because it creates chains between Pokemon
* Added the Underground
  * You need an explorer kit to go to the underground
  * An area beneath Sinnoh to explore and gather rare items in the game.
    * Mining. Players can find a shiny orb at walls, when interacting with them they will play a mining minigame. Players must try to find items in this walls, if you mess up the wall will crumble and it the minigame will end, players must then find another shiny wall.
      * Spheres
      * Fossils
      * Heart Scales
      * Plates
      * Evolution Stones
      * Weather stones
      * Sellable items
      * Odd Keystone
        * This is a unique item to find a Pokemon called Spiritomb. You have to talk to 32 players at the undeground \(you can interact 32 times with the same player\)
        * Once 32 players are interacted you can find a Spiritomb at the Hallowed Tower at Route 209.
    * Players can bury spheres they find at the mining minigame, it's like harvesting berries. These spheres are the currency of the underground
    * Players can bury traps. This are pretty much traps that will alter player's movements. The main use is to sabotage players from getting your flag.
      * Players can see shiny spots on the ground to identify their own traps.
    * Vendors. They offer different items, some offer
      * Goods Merchant \(Items for secret bases\)
      * Traps Merchant
      * Treasure Merchant \(Buys your treasures and gives you spheres\)
    * \[UPDATED\] Secret bases are located in here. 
      * It was upgraded to even  more accesories and you can even find use a PC to look for treasures, buried spheres and traps here.
      * Players can take flags from other players and store them there. Gathering more flags will remove the boulders at player bases. Players can recover their flags in real-time, as it is quite a "capture the flag" mini-game in a Pokemon game.
        * You can recover a flag by interacting with the player that has the flag
        * When you get 50 Flags yu can remove all boulders
        * When you get 50 flags you get a star on your trainer card
* \[REMOVED\] Battle Frontier
  * What? Removed? Yeah. Not present in Diamond And Pearl
  * \[ADDED\] Battle Frontier \[PLATINUM AND JOHTO REMAKES\]
    * What? Added? Once again, this can only mean a business stand point. The frontier is only availiable in the "Special versions".
* Team Galactic
  * Once again we there's a team here.
  * Cyrus goals are to remake the Universe. Which is an insane thing to do, compared to Team rocket, and it's a big step from covering earth with land or oceans like Magma/Aqua.
  * The trio of this game plays a role in the lore of the game in order to create an Item called  "the red chain". The red chain is used to control Palkia/Dialga.
  * I don't have an easy way to recon for how many encounters you have in the game, it's around 10 or more encounters. 
  * Platinum has more encounters than Diamond and Pearl and it expands the story, this time you can enter the Distortion World, you will get help from the Champion Cynthia, you have to make sure that Space and Time won't be destroyed.
* \[UPDATED\] Trainer Rematches
  * The Vs. Seeker is a Key Item you can use to have rematches with other trainers. This item was introduced in Generation 3 in FireRed and LeafGreen, we are not covering deeply remakes, so as a "real" generation game, this is the first time you can use it. It can be used with any trainer that challenges you along the game.
    * Additionally you can have daily battles at the Seven Stars Restaurant and Jublife.
    * You can also battle maids at the Pokemon Mansion
* Your Rival
  * Barry is your rival, he is strong but still friendly. It's a good rival
* Added Gym leader rematches \[PLATINUM AND REMAKES ONLY\]
  * A missing feature in Diamond and Pearl, but it has  been brought back in Platinum and the Johto Remakes.
  * In Platinum you battle them at the "Battleground"
  * The Johto remakes make a better way of fighting gym leaders by using a "facility" called the "Fighting Dojo"
* \[UPDATED\] Game corner
  * While present in Diamond/Pearl/Platinum, in the Johto remakes, and only for the NON-Japanese games, the Game Corner was replaced with "non-gambling" game called the "Voltorb Flip". This is one feature a feature created in order to not introduce gambling to kids.
* Added Multiplayer Avatars
  * You can select which NPC Trainer you want to be. E.g. You can select a Bug Catcher or a Rich Boy
* \[UPDATED\] Pokemon events
  * Non-exclusive Pokemon Events
    * Drifloon
    * Spiritomb
    * Rotom
    * Uxie
    * Mesprit
    * Azelf
    * Dialga \[DIAMOND ONLY\]
    * Palkia \[PEARL ONLY\]
    * Heatran
    * Regigigas
      * Need of the previous generation trio. The regis to encounter this Pokemon.
      * You will permanently lose the trio Pokemon from your third generation games after transfering them.
    * Giratina
    * Cresselia
  * Exclusive Mystery Gift Events
    * The bad thing is that there are Pokemon events that are limited to exclusive Mystery-Gifts \(Eg. Darkrai, Shaymin\)
      * And for the worse part, there was an Event for Arceus, but it was never distributed officially, you can watch a Youtube video about it, if you wanna see how it was supposed to work.
    * Pokemon List
      * Darkrai
      * Shaymin
      * Arceus
* Post game
  * \[REMOVED\] No more trick house
  * Enjoy the Underground multiplayer features
  * You could get all in-game accesories
  * You could get all the Goods from Mr. E Goods.
  * Defeat Charon at Stark Mountain
* \[IMPORTANT\] Heart Gold and Soul Silver Remakes Observations
  * Use of Pokewalker an extra hardware included.
  * Pokemon that change form can change at certain locations in the game.
    * Deoxys
    * Rotom
    * Giratina
    * Shaymin
  * The Pokeathlon \[NEVER SEEN AGAIN IN OTHER GAMES\]
    * Somewhat an equivalent of the Pokemon Contests.
    * \[LOT OF WORK\] Perfomance stats are used. EVERY POKEMON HAS SPECIFIC STATS FOR THE GAME, 493 REVIEWED POKEMON FOR THIS.
      * Speed
      * Power
      * Skill
      * Stamina
      * Jump
    * The goal is to get all the medals
    * These are more fun because they use the Following Pokemon sprites to play here. These minigames are more skill based, they can be kinda compared to the minigames in Pokemon Stadium 1 and 2, if you want to dig a bit more there, but remember we are not talking about those games here, only the core games.

### Generation V

Nintendo DS: 2010

Pokemon Black/White and Pokemon Black/White 2. This is the first time we get two versions of the "special" versions. The good thing about this 2 new versions is that this is a sequel to the first games, meaning that they are considered different games, you even play with different protagonists. This is a good step forward, the bad thing is that they are still releasing 2 different upgraded versions of a previous game, most people would just prefer to get only one game with all the features combined, this can be called an Ethical problem.

* \[UPDATED\] Pokedex
  * \[RECORD\] 156 New Pokemon! The largest amount of new pokemon in a new generation.
  * Unova Pokedex: The 156 New Pokemon are in the regional dex! I personally think this is a great idea, as it gives the new pokemon their time to shine.
  * Use of a Scrollbar to move the Pokemon list in the fully functional Pokedex.
  * Usability has improved over the previous generation
  * National Dex is present and you can switch between the 2 Pokedexes with 1 button
  * \[UPDATED\] Area
    * You can now see how you can find a Pokemon to catch it
      * Walking Grass
      * Surfing
      * Fishing
    * \[REMOVED\] You can't search Pokemon by Day-Night cycle.
  * View different Forms
    * You can see the Pokemon and their different forms in the Pokedex if you see them.
      * Gender forms
      * Special forms \(Like Deoxys\)
      * Shiny Forms, this is brand new. You can now select shiny forms in to display in your pokedex.
  * \[REMOVED\] Height Comparison
  * \[REMOVED\] Weight Comparison
  * \[UPDATED\] Search Mode
    * All gen 4 features seem to be here.
    * \[UPDATE\] Name search can now be used with one letter, instead of three. \(Search for A, instead of ABC\)
* Added Shiny Charm \[SEQUELS ONLY\]
  * Increases chances to find Shiny Pokemon
* Added Oval Charm \[SEQUELS ONLY\]
  * Increases chances to generate an egg at the day care.
* \[REMOVED\] Poke Ball Seals
* Dungeons ~ Total: 26 \(That's quite a lot! And that's not even all the areas in the games\)
  * Abyssal Ruins
  * Castelia Sewers
  * Celestial Tower
  * Challenger's Cave
  * Chargestone Cave
  * Clay Tunnel
  * Dragonspiral Tower
  * Dream Yard
  * Giant Chasm
  * Lostlorn Forest
  * Mistralton Cave
  * Moor of Icirrus
  * N's Castle
  * Nature Preserve
  * Pinwheel Forest
  * Plasma Frigate
  * Reversal Mountain
  * Relic Castle
  * Relic Passage
  * Seaside Cave
  * Strange House
  * Twist Mountain
  * Underground Ruins
  * Victory Road
  * Victory Road BW2
  * Wellspring Cave
* There are 3 trios in this game.
* New Game Version differences
  * Areas
    * Black City ~ Exclusive to Black
    * White Forest ~ Exclusive to White
      * Cosmetic  changes
        * Opelucid City \(Huge difference\)
        * Mistralton City \(Just a single asset\) 
  * Gym leaders
    * Drayden is black only
    * Iris is white only
  * N Battle
    * He will have the other legendary mascot in his party.
* \[UPDATED\] Bag
  * The bag was changed again, I personally think that Gen 4 had better categorization with the 8 Pockets.
  * \[REMOVED\] Poke Balls Pocket
  * \[REMOVED\] Mail
  * \[REMOVED\] Battle Items Pocket
  * The new Pockets are like this
    * Items
    * Medicine
    * TM/HM
      * \[IMPORTANT\] TMs have infinite uses starting from this generation.
    * Berries
    * Key Items
    * Free Space \(Black and White 2 Only\)
      * Good idea!!. Players can place any item they want on this free pocket!
* "New" Pokeballs
  * Still no ways to get apricorn balls
  * \[REMOVED\] Park Ball
    * \[EQUIVALENT\] Added Dream Ball. A New Pokeball with 100% catchrate that can only be used to catch Pokemon from the Dream World.
  * Basically, no new relevant pokeballs, as the Dream Ball is just a gimmick for Dream World.
* \[UPDATED\] PC Storage System
  * Total Boxes: 24
  * Total Capacity: 720
  * Added the Battle Box
    * Place 6 Pokemon in this box, as way to have a quick access for battle features in the various game modes.
* \[UPDATED\] New Evolution Methods
  * Trade 2 specific pokemon for an evolution \(Karrablast and Shelmet\)
  * With Pokemon contests removed and the Condition Feebas can't evolve with the original method, you have to use a "Prism Scale" and trade Feebas to get a Milotic. You can always transfer one from previous generations
  * Location Based evolutions 
    * New locations where they can evolve
* \[UPDATED\] Pokemon battles and capture
  * Pokemon sprites are now FULLY ANIMATED instead of intro animations only present in special version \[Crystal,Emerald,Platinum\]
  * Added Triiple Battles
  * Added Rotation Battles
  * Attack combinations
    * Pledge attacks can be combined and have different effects. \(These seem to be the origin of Terrains moves\)
  * Wonder Launcher \(PvP only\)
    * Use of items for Player versus Player battles. You earn this items along the battle, these are not linked with your bag
  * You can have Double Wild battles \(while this was introduced in generation IV, you had to be with another NPC trainer to do so. This is the real deal\)
    * You can only catch one of the Pokemon in these double encounters, defeat the one you don't want.
  * Shaky Encounters. You will find shaking things in the wild areas, these can have rare Pokemon.
  * Critical Capture. Imagine a critical hit, but when you use your Pokeball. You increase the chance of a critical capture when you have more Pokemon caught in your Pokedex
* \[REMOVED\] Secret Bases
  * \["EQUIVALENT"\] Dream World \[NOT IN GAME\]
    * Sadly this is a huge letdown for this games, as now you require another software to
    * A "new" equivalent but not really. Since you could customize/decorate your "Dream World" Home.
    * Players would send their Pokemon to the dream world \(which   is not even in game, it's a website. \)
* \[UPDATED\] Breeding
  * New Abilities, Hidden Abilities only obtainable at the Dream World.
  * Hidden abilities can be passed down only if the Pokemon with the ability is female
* \[UPDATED\] Move tutors
  * \[REMOVED\] "Cool" tutors are removed in the game. This is, the ones that appear in "special versions". Why does this keep happening?
    * Added "Cool" tutors again. Where? Obviously only for the special versions, at least they are sequels here and just a third version with a few more things.
  * Added tutors for Pledge moves
  * Added a tutor for Keldeo, this move will help to change form
  * Added a tutor for Meloetta, this move will help to change form
* \[UPDATE\] Breeding
  * Holding an everstone guarantees passing a Pokemon's nature
  * Abilities have more chances to pass down to baby Pokemon coming from the Mother
  * Incubating items at the Join Avenue \[Black and White 2\]
* Added New Forms.
  * Basculin has 2 forms. They have different abilities
  * Darmanitan has 2 forms. Changes in battle
  * Deerling has 4 forms. Changes with the game season
  * Sawsbuck has 4 forms \(like Deerling\).
  * Meloetta. Changes with an attack
  * New gender forms
    * Only 3 Pokemon have gender forms here. At least these are more notorious.
    * Unfezant
    * Frillish
    * Jellicent
  * BW2 Exclusive forms
    * Tornadus - Therian Forme
    * Thundurus - Therian Forme
    * Landorus - Therian Forme
    * Black Kyurem
    * White Kyurem
    * Keldeo
* \[UPDATED\] Pokemon Events
  * For this generation there are even more Pokemon events and I added more sections for them. Althought this section is incomplete.
    * Victini
      * Limited, you need a Liberty Pass
    * Reshiram
    * Zekrom
    * Zorua
    * Zoroark along with the chosen Gen 2 Legendary Beast
    * Keldeo
    * Meloetta
    * Genesect
  * Interactable Pokemon
    * Cobalion
    * Terrakion
    * Virizion
    * Landorus
    * Kyurem
    * Volcarona \(Not a legendary and it's awesome to have this in the game\)
    * Musharna \(Not a legendary as well, but interesting because the Dream World its important for this game's lore\)
    * Shiny Haxorus
  * Roaming Pokemon
    * Tornadus
    * Thundurus
* Season Mechanics
  * Each season lasts a real life month.
  * Many areas in the game will have a cosmetic change.
  * Weather can change in specific areas due to another season happening
  * Wild Pokemon will change in different area due to a new season.
  * Some areas will have access to other areas depending on the season. E.g Snow appears in Winter and it will let you walk to a new area.
  * Background music will change with different seasons!
  * Seasons affect how the game changes between Morning, Day, Evening, Night.
    * Imagine like how days and nights are longer depending on the seasons in real life.
  * Certain events with some NPCs change depending on the season
* \[REMOVED\] Pokemon Contests
  * \["EQUIVALENT"\]  Pokemon Musical.
    * \[REMOVED\] Use of battle mechanics.
      * I assume this is because EVERY move has to be reviewed and give it a special effect. Sadly, it was something people enjoyed and it makes it feel as an inferior version of the Contests. 
    * Overall this game-mode feels somewhat empty, it can feel like like an idle-game, since it plays automatically, auto-battlers were not the trending stuff back in this time.
    * 4 Categories
      * Cool
      * Cute
      * Elegant
      * Quirky
    * The total of moves is 559. A lot of stuff to review
    * Props are very similar to what they were in Contests
    * Sections
      * Dress-up \(Like the 4th generation\)
      * Dancing
        * Players can't interact here at all, aside of what props were given to the Pokemon participating
      * Review / Results
    * Rewards
      * After the performance ends, the player can reach the audience outside reception to receive props.
      * Better results mean more props received from the audience.
      * Obtain all 100 props to upgrade the trainer card.
* Added PokeStar \[Black and White 2 Only\]
  * Players do "small objectives" during battles in order to get the best endings.
  * Movies have different endings
  * Create around 12 different series of movies
  * Use of rental pokemon
  * Use of your own pokemon \(unlocked later\)
  * Create movies and rank up to Rank EX \(Rank 1-5 and then Rank Ex\)
  * I think this was an awesome feature of the game, it uses the core battle mechanics to try and do something different.
  * There are movies that YOU DON'T BATTLE POKEMON, you battle a different kind of enemy.
* Important characters battles. You get a rematch every day.
  * You can fight Cynthia who is at Undella town. 
  * Game Freak Morimoto
* Battle Competition
* \[THE BEST SO FAR\] Team Plasma
  * This is probably the best story in a Pokemon game. Team Plasma is up to something, they will be in the story during the whole game, as well as a very interesting character called "N".
  * Team objective is to liberate Pokemon. They are a morally grey team, as it makes sense to think that you are improsining and "slaving" Pokemon when you capture them.
  * This is the most challenging team yet, even if the objective has less impact in the Pokemon world, like Cyrus.
* You get 2 Rivals here at the very beginning of the game.
  * One is clumsy, the other one is more objective. Yet they are your friends. With these 2 you can see why usually people prefer more competitive rivals.
* \[UPDATED\] Pokemon Center
  * Pokemarts are now located INSIDE the Pokemon Centers.
    * \[REMOVED\] Pokemart buildings
  * The Wireless and Internet NPCs are now located upstairs from the Pokemon center, these are located in the SAME ROOM, remember that previously they were located in different in-game rooms.
    * \[REMOVED\] Global Terminal building.
    * The Global Terminal features are now accessible upstairs in Pokemon Center
    * \[IMPORTANT\] Added a new online feature Random Matchup. Get matched with a random player to have a Pokemon Battle.
      * Get matched in Free Mode \("Casual Mode"\)
      * Get matched in Rating Mode \("Ranked Mode"\). This mode is connected with the Global Battle Union
      * You can view your "Player Rating" using the Vs. Recorder Key Item
      * We won't list here all the rules of the online battling as it can be a complete topic of analisis. The important thing here is that players online can have an `emergent PvP gameplay` with random matches.
* \[REMOVED\] Trainer rematches with any trainer of in-game areas.
  * You can just do daily battles at the "Big Stadium" and the "Small Cout"
  * You can rematch "Pokemon Breeders" Trainers on sight.
  * You can rematch certain trainers at the "Royal Unova" Boat, daily.
  * You can rematch trainers on the "Big Dome" and "Little Dome".
    * Battles depend on the time and season
    * Baseball
    * Soccer
    * American Football
    * Tennis
    * Basketball
* \[INTERESTING\] The Unity Tower
  * When you make a trade over the internet it will register the region \(I assume this game keeps track of the Countries now\).
  * Each Pokemon with a new country will be listed at the Unity Tower
* \[REMOVED\] Gym Leader Rematches
  * INCREDIBLE DISSAPOINTING. You might be getting tired of seeing this. Indeed, Black and White removed Gym Leader rematches after doing an AWESOME job with the rematches in HeartGold and SoulSilver. 
* \[INCREDIBLE FEATURE\] Pokemon World Tournament ~ PWT \(Sequels Only ~ BW2\)
  * Did you ever wanted to have content from all regions, all games? This is such an incredible feature, here you can battle characters from all regions. This is pretty much an equivalent of the Battle Frontier for this special versions
  * While Gym Leader rematches were removed, this event marked a high bar of what we wanted to expect fo
  * You can enter as many times as you want.
  * Formats present
    * Singles
    * Doubles
    * Triples
    * Rotation
  * Normal Tournaments
    * Rental. Like the Battle Factory
    * Mix. Using the mechanic of switching pokemon from the Battle Factory.
    * Download Tournaments
      * By using the Nintendo DS Servers, you could download special tournaments, 11 tournaments, although 6 were only for Japan.
  * Special Tournaments
    * Unova Leaders
    * Kanto Leaders
    * Johto Leaders
    * Hoenn Leaders
    * Sinnoh Leaders
    * World Leaders \(All gym leaders can show here\)
    * Champions Tournament
    * Rental Master
    * Mix Master
    * Type Expert \(You can only use Pokemon of specific types\)
* Black Tower and White Treehollow \[SEQUELS ONLY\]
  * Exclusivity
    * Black Tower is Black 2 Only
    * White Treehollow is White 2 Only
    * But here's another thing, a new feature was introduced and player can get the ability to switch the 2 areas. That's right, you can go to the White Treehollow you need the opposite version game to give you a special key. You get this with the `Unova Link Feature`
  * Considered a battle facility, like the Battle Frontier
  * Conquer 10 different areas to defeat the boss at Area 10
  * You can get evolution items depending on the day you play this
* Battle Institute
  * A "Mini Battle Tower" where you will fight 5 trainers and you will get a score and a certificate based on how well you do.
  * Elite Rank / 6 Stars is the Max
* Generation Gadget \(C-Gear\)
  * \[REMOVED\] Most of the Poketch Apps
    * While it's sad that many small features from the the Poketch were removed, it also makes sense that this is when people is starting to get smartphones. Many Poketch apps are already on our phones, our computer or a website. Here's a list of things that your phone has:
      * Any Clock
      * Calculator
      * Memopad
      * Counter
      * Coin Toss
      * Move Tester \(You could just go to a website, or you can learn the effectiveness of attacks, most veteran players know this because battling teaches this.\)
      * Calendar
      * DotArtist \(You can have a better App for drawings\)
      * Roulette
      * Kitchen Timer
      * Color Changer
      * StopWatch
      * Alarm Clock
    * This are the apps that are only useful within the game, since they need the game data.
      * Your Party \(Not really neccesary to have\)
      * Happiness Checker
        * Useful, since there was no need to go and ask an NPC if your Pokemon were happy.
      * \[UPDATED\] ItemFinder. 
        * Useful, and its back as a KeyItem in this genration!, first generation Itemfinders were awful compared to Gen 4 and 5
      * Berry Checker. 
        * Since there's no berry harvesting, this pretty much had to dissapear. This was very useful
      * Day-care checker
        * Useful, but not really neccesary. Remember, people grinding for eggs are always close to the daycare.
      * Pokemon History 
        * Debatable. Probably the most useful feature would be Pokemon that you traded, since those Pokemon left your game.
      * Marking Map
        * Not just Pokemon has this feature, many games have the ability to put markers on your map. Overall is useful, it helps for in-game tracking for stuff. Pokemon doesn't have much tracking needed, but people can always find its use.
      * \[UPGRADED\] Link Searcher
        * This was upgraded to a feature in the C-Gear in this generation.
      * Trainer Counter.
        * Useless. Pokeradar was removed in this generation...
      * Matchup Checker
        * This thing wasn't even released officially. But, a lot of people who are hardcore breeders know matchup compatibilities, if not, people would just check a website.
  * When you turn on the C-Gear On it will search for local wireless and infrared communications. Black and White cartridges have Infrared.
  * Like the Poketch, the C-Gear will be always on your touch screen. You can the tiles to select the 3 communication options
    * Change Tile Icon
    * Change Tile positions
    * Communications
      * Infrared ~ IR
      * Wireless
      * Online
  * Create Surveys
    * Check Results
    * You get rewards depending on the question, like Pokeballs, Medicine, Vitamins, Treasures.
    * Personally I don't think this feature is needed in future games, as this is something people can talk. These rewards are stuff you can buy in game \(except for treasures\).
  * Taglog
    * Displays people playing around. 
    * An improved feature to the Poketch App of the Link Searcher
  * Communications
    * \[HUGE IMPACT UPDATE\] Infrared ~ IR. You can use the C-Gear to instantly battle or trade with someone using infrared. The downside its that it uses infrared instead of the native wireless DS Communications.
    * No need to go to the Pokemon center! You can be in any area of the game and battle or trade wirelessly.
    * Battle
    * Trade
    * Friend Code Exchange
    * Feeling Check
      * Interact via touch screen to see how "compatible" you are with another player. You will be "scored", you can recieve a Heart Sweet tem or two depending on the score. 
      * You can do this once a day with a person
  * Wireless Communications
    * Entralink \(This is how you transport to the entralink\)
    * Xtransceiver
      * Allows you to have a video call \(if your DS has a camera\) or just a simple call with the DS Mic.
      * 4 players can join the call
      * While it's a good feature and probably something that helped them understand and improve their communications knowledge, this is not a feature that it's not missed for the same reasons as why the Poketch can be deprecated because we have smartphones.
      * Black and White 2 Only
        * Mini-games 
          * Balloon Catch
          * Balloon Smash
        * Check happiness values with Bianca
        * Check EVs with Bianca
        * Type Compatibility \(Like that Poketch app in Gen 4\)
        * Calling your rival will tell you locations of where you could find legendary Pokemon. Makes a resemblance on when in generation 2, people will call you on where to find Rare pokemon
        * The Dropped Item QUEST
          * An optional quest to get different Pokemon with hidden abilities
          * The Pokemon you can get DEPEND ON YOUR PLAYER'S GENDER
  * Online
    * Game Sync
      * Defined as "The process of synchronizing the player's save file with the Pokémon Global Link". Well, if we wanna talk about this feature we need to also define what the "Pokemon Global Link is"
      * First, you will upload "save data" to the Global Link and then send a Pokemon to the Dream world.
      * You have to create an separate online account to use the global link. When Game Freak talks about stuff that could be complicated for kids, like the Battle Frontier, it makes me wonder why would you put extra "walls" to access more content in the game. Yeah, kids can use many devices and understand websites, but still this is an extra step, a new wall to let players reach "new content".
      * [Pokemon Global Link](https://bulbapedia.bulbagarden.net/wiki/Pok%C3%A9mon_Global_Link#Generation_V_Global_Link_features) \(A Website\)
        * This has been one of the hardest sections to write in this document. Because the Global Link has been changing and removing features according to when new generation games show up. For example, no one can access the Dream World as of today.
        * Defined as an "internet multiplayer feature in the Generation V, VI, and VII core series games".
        * Login to your account, that way you will use the features
          * Dream World
            * In this generation yoou could go to the "Dream World", here you would get Pokemon with special abilities that can't be obtained in the cartridges. What an awful thing when thinking in long term.
            * Obtain items in the Dream World. You could get berries here, because remember...? Harvesting is was totally removed from this game.
            * You could play mini-games. They removed the in-game mini-games in order to put them in a limited time website.
            * You could "explore the Island of Dreams"
          * Global Battle Union
            * Records statistics on how well you have performed using the Random Matchup feature.
            * There are seaons and you get ranks depending how well you've done it.
          * Profile
            * See your profile from the games, but online
          * Customize
            * Change Skins for:
              * The Pokedex
              * The C-Gear
              * Musical Shows
            * According to Bulbapedia: "These customizations could be set in the game after using the Game Sync feature to wake up a Pokémon from Dream World. ". Which makes me wonder if new players get Pokemon Black, how are they going go customize their Game Sync? Long term speaking, the Global Link seems to do more harm instead of helping. A feature as simple as to pick a skin has been locked. I would appreciate if someone has more information regarding if customization has been locked for new players.
              * Also, many skins are also Time-Limited, they were only distributed at specific dates.
          * E-Z Mail
            * Send and receive mails using preconstructed letters, you just have to fill blanks.
* Hidden grottos \[Black and White 2 Only\]
  * Chances of finding change when you take 256 steps in the game.
  * Small areas where you can find Pokemon with Hidden Abilities. Abilities that pretty much were only possible to get at the Dream World
* \[REMOVED\] Safari Zone
* \[REMOVED\] Pal Park
  * \[EQUIVALENT\] PokeTransfer
    * The HUGE let down is that you require 2 Nintendo DS systems. So, if you have only one at home, then you have to get help from other person with a DS.
    * You transfer from 6 to 6 Pokemon.
    * Restrictions
      * Pokemon can't hold items
      * They can't know a HM
      * You can't send eggs.
      * You can't transfer a special Pichu limited to only HeartGold and SoulSilver.
    * Relocator
      * Transfer event Pokemon from HeartGold and SoulSilver to activate events in Black and White.
      * Catch Zorua and Zoroak
* \[REMOVED\] Berry Harvesting. Yup, they removed this. The berry pots were a great idea, remember? 
* \[REMOVED\] The Underground
  * \[REMOVED\] Secret Bases/My Room
  * \[EQUIVALENT\] The Entralink
    * You can't explore the entralink if you are alone, contrary to the Underground where you could do activities alone.
    * Up to 3 players can connect here
    * Entra Forest. This is where you can catch the Pokemon you found at the Dream World.
    * You will be given Dream Balls to catch them, 100% catch rate.
    * Pass Powers
      * At the center of entralink, you can register Pass powers that will give you more rewards for the various Pokemon Mechanics.
      * You can register a Power in your C-Gear to use it multiple times along your adventures
      * You purchase powers using pass Orbs.
      * You obtain Pass Orbs completing missions.
      * List of mechanics in pass powers:
        * Increase probability of Hidden Grotto regeneration
        * Increase chance of encountering Wild Pokemon \(Sweet Scent seems better than this...\)
        * Decrease chance of encountering Wild Pokemon \(We already have Repels since Generation I, not really neccesary\)
        * Eggs can hatch up to 2x faster \(Incredibly useful for breeder players\)
        * Increase Pokemon happiness \(Useful for Pokemon that require happiness evoluton\)
        * Pokemarts can have up to 50% discount \(If you can have discounts on repels, why would you use the decrease chances of encountering Pokemon? What was the idea behind this design?\)
        * Restores HP of the lead Pokemon up to 200HP \(Why would you use this power when you have medicine items?\)
        * Restore PP of the leading Pokemon \(Usually PP restoring items were limited in-game. This one is most useful so you don't go back to the Pokemon center and combine with a potion\)
        * Increase Exp. Points from a battle up to 2x
        * Decrease Exp. Points from a battle up to 0.5x \(You might think this is not useful, but can work when doing EV training\)
        * Increase Prize Money from battles up to 3x \(And as far as I know, you can stack it with Amulet Coin\)
        * Increase chances of catching Pokemon
    * Missions
      * When people join the Entralink, they can do missions to help other players. 
      * The objective is to interact between the 2 players, pretty much a tag game.
      * There is also an item hiding mission.
      * When you complete 6 missions, the other players will be the one that will be needing help for missions.
      * Completing missions give you Pass Orbs.
      * Support Missions
        * Your mission is to give another player an enhanced version of a Pass Power.
        * You can give them one of these powers
          * Exp. Points from a battle is doubled
          * Prize Money from battles is tripled
          * Eggs hatch faster
          * Happiness increase faster
          * Pokemart discounts for 50% off
          * HP can be fully restored
          * Increase chances of catching Pokemon
  * \[Upgrade\] Funfest Missions \[Black and White 2 Only\]
    * The sequels "enhanced" the original Entralink missions by adding the Funfest Missions.
    * There's more variety of missions, rather than just tag games.
      * Find Berries
      * Find lost items
      * Find NPCs
      * The "Enjoy shopping" mission, players can talk to a Clerk in the Pokemart to have a 50% discount
      * Find a specific number of Pokemon
      * Defeat Trainers \(Only Blackbelts or Ace Trainers\)
    * They can be activated ANYWHERE in the region.
    * You can do them ALONE
    * Instead of a Max of 3 players, you can do this with other 100.
    * Rewards are still Pass orbs
    * Only limited kinds of berries can be found here. Harvesting is still missing.
* \[REMOVED\] Battle Frontier
  * Indeed. The Battle frontier has been removed from the game. This was a huge thing for post-game, so now post-game has been reduced.
* \[REMOVED\] Battle Tower
  * \[EQUIVALENT\] Battle Subway
    * Just another name for the battle tower.
    * Added the "Super" formats
      * Unlocked after obtained the National Dex and having a 21 win streak.
      * Super format has different trainers than the normal train.
      * Super format use Pokemon from all 5 generations.
    * Bosses are Ingo and Emmet
* \[UPDATED\] Trainer Card
  * Defeat Ghetsis and Team Plasma
  * Complete the National Dex, excluding the Mythical Pokemon
  * Collect all 100 Pokemon Musical Props
  * Obtain all 33 Entralink pass powers
  * Defeat Ingo and Emmet on the Super Single and Super Double Battle Subway
* Join Avenue \[Black and White 2 Only\]
  * A building that will level up and will get special items in the various shops
  * While it's a nice addition to the game, even upgrading this facility is a big of a chore, you will level this up by interacting with other players, sharing some similarities of the Flags at the Underground \(Gen 4\). You can't really level up this facility playing just by yourself, so, its a bit of a downside, players need options.
  * Shop types
    * Beauty Salon
      * Increase Pokemon happiness like in previous generations
    * Cafe
      * Items that increase Pokemon stats
      * Items that increas e Pokemon levels
    * Dojo
      * Increase Pokemon levels
      * Increase Pokemon stats \(EVs\)
    * Florist
      * Sells sets of various berries \(remember, there's no harvesting here\)
    * Raffle Shop
      * \[EQUIVALENT\] Lottery ID from previous games
    * Market
      * Closest thing to a Pokemart, althou its debatable "better"
    * Nursery
      * Items that help hatching eggs
    * Antique Shop
      * Random selection of items
      * Pokeballs
        * Still No Apricorn balls, that were missed since generation 2 \(or 4 as remakes\)
      * Evolution Stones
  * You can only purchase 1 item of each kind every 24 hours
  * Some NPCs are fans and they give you items
  * Customization
    * Change avenue name
    * Change your title
    * Change your phrase
  * Max Avenue Level is Level 100
* \[UPDATED\] Experience
  * Experience calculation has been changed for the first time after 4 generations. Your Pokemon level, the enemy Pokemon level is taking into consideration with this new changes.
* \[SURPRISING FEATURE\] Medals / Achievements \[Black and White 2 Only\]
  * Something we knew from Nintendo games during the 360 and PS3 era, was the fact that Nintendo didn't have built-in achievements, as it was somewhat drifting away from their game philosophy, yet Pokemon Black and White 2 added this feature.
  * There aree 200 Medals available in the game
  * This improves the completion sense
  * This can help with the post-game content
  * Helps progress tracking
  * Medal types
    * Special Medals
    * Adventure Medals
    * Battle Medals
    * Entertainment Medal
    * Challenge Medal
* Unova Link
  * \[IMPORTANT\] Key Link
    * Special "keys" to activate different features in the game.
    * Capacity of changing the game's difficulty.
    * Capacity to change the version exclusive areas, to the one of the other version. \(Black City to White Forest and vice versa\)
    * Change the Regi Pokemon areas.
      * The 2 different version can give the opposite key to catch the Regi that is not featured in the game.
      * I believe this is an interesting feature. An important observation that Pokemon veterans know, it's the fact that legendary pokemon are limited to 1 per save-file. These keys enable players to make their own save file to get their own legendary pokemon. You enable this Pokemon by trading keys with other game-versions.
      * Imagine that you could get in your version the other mascot of the game, and not just stick with your own mascot, with this idea, player's would have to work their way out in order to obtain these keys.
  * Memory Link
    * Connect with the first games, Black and White 1. This allowed continuity to make much sense between this generation
    * Flashbacks, you get the opportunity to know how some characters that appeared in the first game conveyed to what they are doing at the sequels.
    * Capacity to catch N's pokemon from the previous game, since N released his Pokemon, as this was his treat Pokemon, something truly unique in this generation. Personally, N was an amazing character.
    * Get all your props from your previous game.
      * Another thing never seen. Instantly carrying over progress from a previous game.
    * Get your items from Loblly's
    * Mention of your Black and White 1 trainer with their name.
      * Certificates and Throphies can be seen in this game too.
      * If you complete everything in this game as well, you can see your throphies from BOTH GAMES.
    * Battle with Bianca
      * Her initial Pokemon changes depending on the one you chose IN THE FIRST GAME.
    * Battle with Cheren
      * Same as Bianca
  * \[UNETHICAL\] Nintendo 3DS Link
    * Allows you to bring items and Pokemon from the "Pokemon Dream Radar".
    * I don't appreciate this feature at all. They knew that at some point the Dream World website would be deprecated, the "Pokemon Dream Radar" is an external PAID APP for the 3DS. I think this was a very unethical move from Game Freak.
      * This makes Pokemon with Hidden abilities blocked behind a paywall of 3 dollars.
      * 3 New Forms for existing Pokemon blocked behind a paywall f 3 dollars.
  * The Unova Link is probably one of the features that also helped raise the expecations bar for the games. Who knows, this could probably be called the Golden Era of Pokemon from Generation 1-5. There's so much content in the fourth and fifth generation.

[Return to Navigation](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#quick-navigation)

### Generation VI

Nintendo 3DS: 2013

* This is the first full fledged 3D graphic game.
  * As expected for 3DS games, they were to implement depth 3D. Sadly these games only used hardware 3D in specific places.
  * 3D was present in Pokemon Battles
* Sadly these games were notorious to have frame-drops. Even turning on the 3D mode would hurt frames.
* Added the Fairy type.
  * Remember: Last time types were added was back in Gen 2
  * Like Second generation, Pokemon were reworked with this new type. \(Eg. Jigglypuff is now Fairy Type \)
  * Total Types: 18
* \[UPDATED\] Player movement.
  * After 5 generations, players can now move in 8 different directions, when walking and running.
  * Added Roller Blades
    * You can perform tricks but you need to unlock them from NPCs
      * 5 tricks in the game.
    * \[IMPORTANT\] Roller blading tricks can also open new areas, as with new tricks you can reach new places.
  * When using rollerblades and the bike, has the 360 movement freedom.
* \[UPDATED\] Pokedex
  * Added 72 New Pokemon
  * The Regional Pokedex has been split into three
    * Central Kalos Pokedex: 153
    * Coastal Kalos Pokedex: 153
    * Mountain Kalos Pokedex: 151
  * \[REMOVED\] Pokemon's footprint
  * There's a button that change the Pokemon mode between Central, Coastal, Mountain, National.
  * Unlock the National Dex after getting in the Hall of Fames
  * Another UI revamp, the touch screen is used to move in the Pokedex.
    * Top Screen is always showing the Pokemon data.
  * \[UPDATED\] The Weight Comparison
    * While you can't compare height with the player, you can compare the weight with any other Pokemon you want.
  * \[UPDATED\] Search Mode
    * Added a new "Shape" filter, which works like the "form" filter in previous games.
  * Height comparison is missing in X/Y
  * OR/AS \[REMAKES\]
    * \[REMOVED\] Weight Comparison
    * Top Screen arranges Pokemon with their Pokemon Icons. 
    * Height comparison is back, the way it was on the original game. Compares size with the player trainer.
    * Search Mode
      * Added Appeareance filter
        * Filter Mega Evolution Pokemon
        * Filter Shiny Forms \(You can officially list Pokemon in Shiny Forms\)
      * Added Encounters filter
        * Has been caught
        * Not yet caught \(Official in-game to list what you are missing\)
* Added Trainer Clothes and Hair customization
  * This marks the start of a new era, where players can have different trainers and not be a clone of the original male and female trainers.
* \[UPDATED\] Shiny Pokemon chance has changed to 1/4096, chances have been doubled. Shinies are less rare now.
  * Added Chain fishing. You can fish and get Shiny Pokemon
* \[REMOVED\] Exclusive version areas \(Black City/White Forest\)
* \[REMOVED\] Pass Powers
  * \[EQUIVALENT\] O-Powers
* Dungeons ~ Total: 14 \(Here's another reason why this becomes Silver Age of Pokemon. We got even less Dungeons than the previous generation, although is slightly understandable with the whole transition from 2D to 3D. \)
  * Connecting Cave
  * Frost Cavern
  * Glittering Cave
  * Kalos Power Plant
  * Lost Hotel
  * Lysandre Labs
  * Parfum Palace
  * Poké Ball Factory
  * Pokémon Village
  * Reflection Cave
  * Santalune Forest
  * Team Flare Secret HQ
  * Terminus Cave
  * Victory Road
* Added Photo-spots
  * Take a photo of  your trainer at specific locations. \(12 locations\)
  * You can
    * Change brightness
    * Change focus
    * Zoom In
    * Zoom Out
* \[UPDATED\] Vs. Recorder
  * You can store up to 100 videos.
  * \[IMPORTANT\] Mock battles
    * You can re-play a simulation of the battles you saved.
    * Used particulary to create simulations and train yourself to the teams you fought against.
* \[UPDATED\] Bag
  * Reverted to the Black and White slots
  * \[REMOVED\] Free Space bag
  * Until now, the 4th generation has the best bag. But the free space bag was also a great feature because every player could add whatever they want, and yet it was removed for "REASONS".
* Poke Radar is back, after it was removed from Gen 5.
  * There are decoy patches, these will also help and tell you that you will break the chain here.
  * There's a possibility for the music to change after a pokemon battle, this music means that there's a high chance to find a shiny Pokemon.
* Pokeballs
  * \[UNOBTAINABLE\] Dream Ball. No more ways get to ge these balls, they are still stored in the game's data when you transfer old Pokemon. Pokemon no longer cares about the dream world, considering how the Global Link removed the dream world as well.
  * Apricorn balls are still missing since Johto

    \[UPDATED\] PC Storage System

  * Total Boxes: 31
  * Total Capacity: 930
* \[UPDATED\] Evolution Methods
  * Have a Pokemon of an specific type in your party.
  * Rotate upside down your 3DS
  * Have bonding using Pokemon Amie
  * Level up during rain
* \[UPDATED\] Pokemon Events
  * Snorlax
  * Lapras
  * Xernas \[X ONLY\]
  * Yveltal \[Y ONLY\]
  * Zygarde
  * Mewtwo
  * One Legendary Bird Roams
* \[UPDATED\] Pokemon Battles
  * \[IMPORTANT\] Added The Mega-Evolutions
    * Total of 50 mega-evolutions \(with Primal Reversion\) with the remakes
    * Need of a special item that has to be held in order to enable mega-evolution/primal-reversion.
    * Only one mega-evolution is allowed for each player.
      * Primal Reversion is different. If for some reason you KO Groudon or Kyogre and you manage to revive them, they will go back
    * You can have a Mega-evolved Pokemon and the Primal Reverted Pokemon AT THE SAME TIME.
  * Added Horde Encounters. Encounter 5 Pokemon at once.
    * Useful for EV training
    * Useful to generate more Pokemon and get a chance for a Shiny one.
  * Inverse Battles
    * Fire beats grass? I don't think so, Grass beats Fire. This is a game move that inverts type effectiveness, flipping game mechanics introduced in generation 1.
    * This is only for Single Player
  * Sky Battles
    * Battles where you can only use Flying Type Pokemon or Pokemon with Levitate
    * Single Player Only
  * For the first time since Gold and Silver with a change like the Special Split.
    * 29 Pokemon have been rebalanced in their base stats.
  * \[REMOVED\] Wild Double Encounters
* \[REMOVED\] Dream World
* \[REMOVED\] Join Avenue
* \[REMOVED\] Pokemon World Tournament
* New Forms
  * Mega-evolutions ~ Total: 50
    * 28 New Megas in X/Y
    * 20 New Megas in OR/AS
    * 2 Pokemon Primal reversion
  * Gender differences
    * Meowstic
      * Different designs.
      * Different move
    * Pyroar
      * Different Design
    * I think we can see here how it's probably an issue for their development streamline to keep adding more gender differences. Generation 4 introduced a lot of differences and only 2 new Pokemon got them. At least they are very notorious changes.
  * Vivillon. 18 skins \(plus 2 exclusive event patterns... for a total of 20\). Somewhat similar to Shellos. In the fantasy, this could have been a Regional Form, since the Patterns are geographical based in our world, not the pokemon world. If this took place in the Pokemon world it could have a pattern per region and even universes. Same stats, different pattern, I will consider this skins, much harder skins, not just a recolor, but to keep consistency, skins.
  * Flabébé. 5 Skins. It depends on which Flower patch you find the Pokemon. Red, Yellow, Orange, Blue or White, like Arceus, and Genesect. It's just a recolor, not a redesign. You can't change the form.
  * Floette. 5 Skins. Evolve Flabébé.
  * Florges. 5 Skins. Evolve Floette.
  * Furfrou. 5 Cosmetic Redesign Forms. They are very different visually, and stats stay the same. But this was more work from the creative team, as this is not a recolor or a harder tweak like Vivillon.
  * Aegislash. 2 "Forms". It's not 100% a form, it's called stance, gotta keep consistency. The idea here would be to think how the Pokemon would look when attacking or defending. This is similar on when you create a character and you have to know how does it look when its happy, sad, angry, etc. Stances changes its stats, and it will not be considered a real form.
  * Special case: Pumpkaboo and Gourgeist. "4 Forms each". Not really forms, but more like different sizes.  If the size is different, the stats will change. Nothing to do here from the artistic point of view. Code-wise you just change the scale of the model.
  * Xernas. "2 Cosmetic Forms". These are fantasy forms. When in battle Xernas has a "Active Mode" Skin, and when it's outside battle is in "Neutral Mode" Skin. 
  * Hoopa. 2 Forms. Using a Prison Bottle it will change its form, identical to Shaymin. Design changes, stats changes and even types changes.
* Pokemon Events
* \[REMOVED\] Seasons
* \[REMOVED\] Pokemon Musical
* \[REMOVED\] PokeStar
* \[REMOVED\] Medals/Achievements
  * They are only available at the Pokemon Global Link website. And by the time you are reading this article, they are not present.
* \[REMOVED\] Difficulty Options \(from the Unova Link\)
* \[REMOVED\] C-Gear
  * \[EQUIVALENT\] Player Search System ~ PSS
    * The evolution of the C-Gear. This device has a social screen where it lists all your:
      * Friends \(Static\)
      * Acquaintances \(Static list that are not your friends\)
        * People you have interacted with in the various social features.
      * Passersby \(Dynamic, changes constantly\)
        * Random people that is connected in the game either Online or Local
    * \[IMPORTANT\] Generation V removed the need to go to the Pokemon Center to do local wireless activities, like trading and battling.

      Now, Generation 6 COMPLETELY removed the need for the Pokemon center as the threshold for these activities.

    * Access the Battle Spot
      * Random Matchup
      * Online Competition
        * Inclusion of Penalties for disconnection
    * Wonder Trade
      * Send a Pokemon and receive a Random Pokemon from another trainer.
    * Global Trade Station
      * Since the Pokemon Center no longer is the threshold for these features, you can find the GTS in the PSS.
    * Access the Game Sync from here, just like Gen 5.
    * Shout Out
      * Broadcast a small message your friends and local players
    * Holocaster
      * Provides news from the Global Link
      * Uses AR to `superimpose` an image so players feel like they are seeing a holograph.
    * Trainer PR Videos
      * A customized 10 second video that player create.
    * Your profile
      * You can set
        * An Profile Image
          * You can select an Icon
          * You can select an Image from the 3DS photos
        * A personal message
        * Questions
          * How do you spend your free time?
          * What's your nature?
          * What's your favorite Pokemon type?
          * What do you like about Pokemon?
          * How do you like to battle?
          * What is your favorite color?
      * Other stats
        * Activity History
        * Location
        * Like Battle Wins
        * Total Like Trades
        * Play time
* \[UPDATED\] Breeding
  * Mothers now pass the Pokeball they were caught
  * Fathers have a small chance of inheriting Hidden Abilities
  * Destiny Knot now inherits 5 IVs instead of just 1
* \[UPDATED\] Experience Mechanics
  * Exp Share is now a Key Item, it not a Hold Item anymore.
  * Exp Share can be turned on or off.
  * Exp Share awards experience to all Pokemon in your party.
    * Pokemon that participated will get 100% of the Exp.
    * Pokemon that didn't participate will get 50% of the Exp.
  * If your Pokemon has high affection it get extra Exp.
  * If a Pokemon reaches its Evolution level \(Eg. Charmeleon is level 36\), that Pokemon will get more experience until you evolve it.
  * Catching Pokemon now awards experience
* Added Rideable  Pokemon
  * You can ride Non Player Pokemon at certain areas. Some of them are used to open the path to new areas.
    * Gogoat
    * Rhyhorn
    * Skiiddo
    * Mamoswine
    * Lapras
* Transfer Pokemon from Generation 5 to 6
  * Overall it's a good thing, sadly this requires an internet connection
  * You have to download a 3DS App called "PokeTransporter".
  * It's also called an "extension" for Pokemon Bank
  * NO LONGER NEED OF USING 2 NINTENDO SYSTEMS.
  * What this App does is that takes your first Generation V Storage Box and it will transfer the Pokemon from that Box over to Pokemon Bank. Then, at Pokemon Bank you transfer your Pokemon to the Sixth Generation
  * \[IMPORTANT\] Pokemon Bank is a subscription based App.
    * We have to be aware that it's highly possible that Pokemon Bank will be probably cease support at some point, and this will make impossible to send Pokemon from generations 3-5 to 6.
* Pokemon-Amie
  * Probably the "closest" but not quite equivalent of Contests or the Musical
  * You can pretty much ignore this feature during your whole playthrought.
  * Pet Pokemon
  * Feed Poke Puffs to Pokemon
  * Participate in contests raises affection in the Gen 3 remakes, which is why I call this thing the closest thing to the contests.
  * New stats that are not hard-linked to battles. Values from 0-5
    * Affection \(DIFFERENT FROM HAPPINESS\)
    * Fullness
    * Enjoyment
  * Pokemon retain affection even if sent to Pokemon Bank or another version.
  * Making Faces Minigame
  * Walking decreases a bit fullness, but increases enjoyment
  * The Pokemon Amie Space
    * A somewhat equivalent of "My Room"/Secret Bases
    * You can decorate \(new customization feature\) the space.
    * Set up to 30 decorations
    * Change the wallpaper
  * At the same time, you might be asking "What is relevant about affection?", does affection benefit in something other than a new "ghost" stat? Here's what it can do
    * Pokemon can gain 1.2x more experience
    * Pokemon can use survive KO hits, think of they automatically use "Endure" because they love you
    * Pokemon can avoid attacks, even moves that have 100% accuracy. Because the game can get even easier now.
    * Remove themselves status conditions at the end of the turn
    * Higher chance for critical hits
    * Different battle dialogues
  * Pokemon from Friends, Acquaintances and Passerby can visit the player's Pokemon.
    * They can "Start" a discussion between pokemon.
    * TWhen 3 Pokemon have a discussion they can leave a gift. Gifts can be
      * Poke Puffs
      * Interior Items
      * Wallpapers
  * This mode has more internal "backend" rules but that's not what we are listing and discussing here.
* Poke Puffs
  * These are not equivalents to Pokeblocks or Puffins. Remember that the condition stats were removed.
  * Increase Fullness and Affection.
  * Obtained from:
    * Playing minigames
    * Gifts from Visitor pokemon
  * 5 different levels
    * Basic
    * Frosted
    * Fancy
    * Deluxe
    * Supreme \(These are obtained in in-game events\)
  * As a cool detail, "Cocoon" Pokemon can't eat Poke Puffs.
* \[REMOVED\] Team Plasma
  * Added Team Flare
    * According to bulbapedia: "Their goal is to create a "beautiful and better" world while making money, eliminating everyone who does not follow their standards."
      * "Lysandre reveals Team Flare's plans of using the "ultimate weapon", a machine built by the king of Kalos 3,000 years ago that can eliminate all life. To achieve this, Lysandre plans to use XerneasX/YveltalY to activate the machine in Lysandre Labs in Lumiose City. "
* Post-game
  * There's a 5 chapter post-game story.
* Move Tutors
  * \[REMOVED\] Cool tutors. For now we can see the trend that only the "Special/Upgraded" versions of each generation will get the better move tutors.
* Added Friend Safari
  * Once again, the safari zone is not present in the games.
  * A Zone where you can encounter different Pokemon based on your friends.
  * Each player is assigned with a set of Pokemon that can show at other player's games.
  * Pokemon can have Hidden abilities here
  * There are 54 Pools of Pokemon. Each Player gets assigned a Pool and IT CAN'T NEVER BE CHANGED.
  * If you have more friends, you have more Pools available.
* Added Super Training
  * Minigames to increase Pokemon's EVs
  * You can also use "training bags" after completing mini games that you can use in the touch screen to increase their stats.
  * Secret Super Training allows you to not only get training bags, but to get rare items.
* \[UPDATED\] Downsing Machine
  * Downgraded. It has become a key item again.
  * You can only walk/run with it.
  * Can't use rollerblades
  * Can't use the Bike

    -A small laser indicator will tell you how close you are to a hidden item.

  * Overall it's a downgrade from the previous iteration, as the previous iteration was visual feedback on your touch screen and had more movement options.
* \[REMOVED\] Battle Subway
  * Added Battle Maison
    * This generation's "battle tower" is called the Battle Maison. This facility has more formats, each format has their own leader/boss.
      * Single
      * Double
      * Multi-battle \(Doubles with a friend\)
      * Triple
      * Rotation
    * The battle frontier or equivalent is nowhere to be seen.
* Added the Battle Chateau
  * While the Vs. Seeker is missing, the most essential feature of the Vs. Seeker is the fact to keep having PvE Pokemon battles during the post-game. This building allows you to do that, similar to other buildings in Generation 5.
  * Trainers come every few hours
  * There are 6 Ranks
    * As you progress you can rematch Gym Leaders, from Rank 4 and up.
* Added Berry Fields \[Berry Harvesting is back\]
  * Added Mulch
  * South of Route 7 is the ONLY AREA where you can harvest berries, there's a lot of soil where you can do so.
  * This is the best iteration of Harvesting, considering as "harvesting in a game map", yet the Berry Pots from the Johto remakes could be improved as well, and be able to have a lot of Berry Pots in the game and be able to manage them in no matter where the player is located.
* Kalos Cafes
  * At the cafes you can talk with other people that can talk to you about Pokemon they've seen and they will be marrked in your Pokedex as seen, this can help you to capture them later \(except for Legendaries\)
* You can customize the battle backgrounds \(you know, that screen where you choose between Fight, Bag, Pokemon, Run.\)
* Capacity to recieve gifts using the "Pokemon Link". Apparently only Pokemon Bank has used this feature.
  * You can receive Pokemon
  * You can receive items
* Added Capacity to Update games with Internet patches.
  * Thanks to the 3DS these games can now be patched.
  * A total of 5 patches were offered in the game.
  * No Special Versions for X/Y were distributed.
  * There were theories of people thinking that we would not see special versions again, since the new "special content" could be offered as DLC \(Downloadable Content\)
* Trainer Card Upgrade
  * Defeat the Elite Four
  * Complete the Regional Kalos Deex
  * Defeat one Battle Maison at the 50th streak.
* Omega Ruby and Alpha Sapphire 
  * As mentioned before, the document doesn't center much in the remakes, but there are features that people notice and want to go back that were introduced in the remakes. Remember that many features of these games are already listed in theirr correspondending section.
  * \[REMOVED\] Player Trainer customization. Because during the third generation there wasn't any customization.
  * Added Cosplay Pikachu.
    * This special Pikachu can't be transfered to other games.
    * A Special pikachu centered to Pokemon contests.
  * Added "Horde" Trainer Battles
    * Pretty much used for team grunts.
  * Added Sneak Movement.
    * Players can "sneak" by gently pushing the circle pad and not reaching to the full tilt.
  * Primal reversion is introduced here, it is then also possible to use in Gen 7. But it doesn't exist in Pokemon X/Y.
  * Added the capacity to Fly in the region and controlling where you want to go, instead of instantly reach your destination. Called "Soar in the sky"
    * Objectively it's not a needed and core feature, yet many players loved this feature as well. It can be enhanced by adding even more places to explore.
    * \[UPDATED\] Mirage Island
      * The Mirage Island has been reworked and now you can access to different mirage locations when you soar in the sky.
      * Mirage Islands
      * Mirage Forests
      * Mirage Caves
      * Mirage Mountains
      * Mirage Spots with Legendary Pokemon
  * \[UPDATED\] PokeNav to PokeNav Plus
    * \[REMOVED\] PokeRadar from X/Y
      * DexNav a much BETTER Pokeradar. Once again, the bar has been set high once again for what player should expect in new games. 
        * An in-game app that lists the Pokemon in an area.
        * EVERY AREA in the game with Wild Pokemon is trackable.
        * You can search for an specific Pokemon by tapping the Pokemon Icon in your touch screen
        * Keeps track of your progress of each area with a Crown Icon. A White/Platinum Crown means you've caught everything in that area.
        * Using the search feature is very similar to the PokeNav, you can even search in caves and is still used to Shiny Hunt.
        * Here's another reminder in the document that many of this systems are more complex on the inside and that players have been making many tests to see how they behave and how to use this systems to fulfill their special needs with their game-style. For example, for this system, there's a lot of Shiny Hunters that want to have a Shiny Living dex.
    * AreaNav
      * The best iteration of Town Map so far. You can see your player icon moving in the map. Although its still not a minimap, it uses the whole Hoenn Map.
      * It can list secret bases
      * It can show you in the map which Trainers are ready to rematch you.
      * It can list Pokemon from the DexNav.
      * You can zoom-in a bit.
      * It also lists berries
      * Trainer rematches are available here, just like the original third generation games.
    * PlayNav \(Encapsulation of X/Y features\)
      * EVERY FEATURE OF THE PSS FROM X/Y IS HERE. What does this tell you? It's Quality of Life enhancements. You are now playing the third generation of Pokemon with the many enhancements that new generations have brought. The PSS is a great system that players love.
      * Pokemon Amie is located here
      * Super Training is located.
    * BuzzNav
      * Similar to the holocaster in X/Y it tells you news from the game, as well as Online News.
      * It also is like watching the TV since generation 3 games, why go to a TV when you have a Mobile device?
  * \[UPDATED\] Secret Bases to Super Secret Bases
    * Flags are used, like in the 4th generation.
      * You have to get 1000 Flags to get the Max Rank
    * Share Secret Bases
    * Secret Base trainers. Battle trainers from other bases.
    * Secret Pals. Recruit players to your own secret base.
    * Special Skills. These are skills that secret pals can perform. 

      These can be considered a sub-set of O-Powers.

      * Massage Pokemon
      * Makee some goods
      * Pick Something up
      * Take care of an Egg
      * Do some training
      * Do some exercise
      * Gather berries
      * Pick up stones
      * Search for treasure
      * Tell my fortune
  * OR/AS had a great post-game story called "Episode Delta", which could be considered the new stuff that could be added to a game called "Pokemon Delta Emerald". Why make a third version when you can add that content to the original games? It was a nice touch and it expanded the lore, multiple universes where confirmed within this post-game.

[Return to Navigation](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#quick-navigation)

### Generation VII

Nintendo 3DS: 2016

Here's the next list of features, covering the Seventh generation. Only Sun/Moon and the Ultra Versions. Pokemon Let's Go will be totally ignored as they are not core games, they can fit the same category as Pokemon Stadium, Stadium 2, Battle Revolution but even more to the Colosseum and XD games.

* \[REMOVED\] Voice chat communications. Things introduced in Diamond and Pearl.
* \[REMOVED\] Support for 3D Depth
* \[REMOVED\] Gyms
  * First time that there are no Gyms in the game.
  * \[EQUIVALENT\] The Island Trials and Grand Trials
    * While it's pretty much very similar to gym, there are only 4 grand trials.
    * This is the first Pokemon League.
* Added "Z-Trainers".
  * Trainers that will only challenge you after you have defeated all trainers in a specific route.
  * This is the first time the games incentive to defeat all players in a route.
* \[UPDATED\] Pokedex
  * \[REMOVED/IMPORTANT\] The National Dex Mode has been removed from the game.
    * \[IMPORTANT\] Even if there's no listing of the National Dex, YOU CAN TRANSFER ANY OF THE PREVIOUS 721 POKEMON TO THE GAME.
  * In this generation your Pokedex is a Rotom.
  * \[REMOVED\] O-Powers
    * \[EQUIVALENT\] Added Roto Loto Items \[ULTRA VERSIONS ONLY\]
  * Added  81 New Pokemon
    * New Alolan Forms for Kanto Pokemon \(17\)
      * Ratatta
      * Raticate
      * Raichu
      * Sandshrew
      * Sandslash
      * Vulpix
      * Ninetales
      * Dugtrio
      * Meowth
      * Persian
      * Geodude
      * Graveler
      * Golem
      * Grimer
      * Muk
      * Exeggutor
      * Marowak
    * New Kind of Pokemon, Ultra Beasts
  * \[REMOVED\] A useful Scrollbar
    * You can only move the list of Pokemon, why would you remove a better way to navigate the Pokedex?
  * \[REMOVED\] The Pokemon data is at the Top screen
    * The Pokedex now can list evolution lines together on the top screen.
    * The Top screen shows the "rarity" of the Pokemon, I'll give classifications
      * Common: Blue
      * Rare:  Green ~ A bit of Glimmer on their names
      * Legendary: Gold/Yellow ~ A lot of Glimmer on their names
    * You can generate a QR Code for "No-Special" Pokemon. With the previous `Rare` and `Legendary` Pokemon are considered `Special`
  * Just like in Kalos, the Regional Dex has been split. Since this game takes place in 4 Islands, there are 4 Sections, plus the whole Alola Pokedex.
    * Melemele Pokedex
      * Sun/Moon: 120 Pokemon
      * Ultra Versions: 150 Pokemon
    * Akala Pokedex
      * Sun/Moon: 130  Pokemon
      * Ultra Versions: 160 Pokemon
    * Ula'Ula Pokedex
      * Sun/Moon: 130  Pokemon
      * Ultra Versions: 160 Pokemon
    * Poni Pokedex
      * Sun/Moon: 100  Pokemon
      * Ultra Versions: 130 Pokemon
    * Alola Pokedex Total: 
      * Sun/Moon: 302 Pokemon
      * Ultra Versions: 403 Pokemon
  * \[REMOVED\] Height Comparison
  * \[REMOVED\] Weight Comparison
  * \[UPDATED\] Area/Habitat
    * When you look for a Pokemon in this game, the map tells you where EXACTLY you can find the Pokemon, the exact grass patches, or the exact place to fish and look for the Pokemon you want.
    * It's a 2-side feature, because while it helps to find a Pokemon  and players can easily try to find them, on the other side, it removes that sense of exploration and patience to experiment on where you can find that Pokemon in a specific area.
  * Added touch screen interactions when playing the game.
    * When you move and explore, you can touch the Pokedex \(Rotom\) and it can talk to you. 
    * Tapping on the top section will immediatly open the Pokedex
    * Tapping Rotom's eyes can be considered as "Petting"

      -\[UPDATED\] Town Map now within your Rotom Dex

      * An even enhanced version of the AreaNav from the Remakes, you can see exactly where you are on the map.
      * There's an arrow that points where you are looking at.
      * What you see on the touch screen at first it's a minimap.
        * Tapping the Map section will open a new screen with a detailed section of the map, like any Town Map since generation 1, but since this is generation 7, there's even more information about thing.
* \[REMOVED\] Alola and Johto are the only regions that didn't introduce new Fossils.
* \[REMOVED\] Roller Blades. And with them, more exploration mechanics.
* \[REMOVED\] Field Moves \(HMs and others\)
  * Any kind of field move has been removed from the game. A first impression to people would that this could eliminate exploration in the games, but not neccesarily, there can be other game design systems to replace the field moves, which, they actually were implemented in the game. Sadly there are many moves that are missing in the game, and in fact, yeah, some exploration has been removed from the game.
  * \[EQUIVALENT\] Added Ride Pokemon
    * Here's a list of the Ride Pokemon available in the game and their HM equivalents.
      * Tauros Charge
        * \[REMOVED\] Bike. As weird as it gets, there's no bike in generation 7. But still, this Pokemon is very fast, the only downside it's that your collision mesh is now bigger and there are places where you have to hop off from Tauros, walk and then ride him again
        * \[OLDER EQUIVALENT\] Rock Smash
      * Stoutland Search
        * \[REMOVED\] Downsing Machine.
          * While it is creative and it makes sense to use a Pokemon to help you find hidden items in the game. The problem is that the bar was set high before in Generation 4 and 5 using the touch-screen dowsing machine it was very intuitive to use the gen 4-5 downsing machine. So, this only gets good points because it's nice to ride a Pokemon
        * A little bit faster than running.
      * Mudsdale Gallop
        * Slower than running
        * \[OLDER EQUIVALENT\] Rhyhorn rideable pokemon from generation 6. You could walk on `Rocky Terrain` using that Pokemon. Mudsdale fulfills the same role.
      * Machamp Shove
        * Slower than running
        * \[OLDER EQUIVALENT\] Strength
      * Lapras Paddle
        * \[OLDER EQUIVALENT\] Surf. Finally it's canon that you ride a Lapras for Surf
      * Sharpedo Jet \(This thing also existed in OR/AS\)
        * Think of it as the Bike when you are in water.
        * It is also Rock Smash, but with Rocks on water.
      * Charizard Glide
        * \[OLDER EQUIVALENT\] Fly
* New Forms
  * Greninja. 2 Forms \(Ugh...\). Okay, this other form is a very different one. While Greninja debuts in the 6th generation, it gets a new form in the 7th generation. The thing is that only if you get a Greninja with the _Battlebond_ ability, then you can have this special form. There are 2 things that I don't like about this form, it changes its stats by a lot, plus the _Water Shuriken_ move will always hit 3 times, but the worst thing about this \(personally\) is the combination of better stats plus the fact that its appearance resembles Ash, from the Anime. Anime and games are different stuff, the Ash resemblance makes me think this is Digimon. \(Note: I also like Digimon, but this is Pokemon, so, I don't like the Ash thing here\)
  * Zygarde. 3 Forms. In 6th generation it only had one form. In 7th generation it got 2 more. The 6th generation form is the "50% Forme", it looks like a Snake. 
  * Fans often made theories that Zygarde's story content was cut from the sixth generation. Players had to wait until the 7th generation to know more about this Pokemon. It even became a sort of a gimmick in the game, where you had to collect the cells and cores of the Pokemon.
  * A Dog like form is called "10% Forme" it has different stats. 
  * A humanoid form is called the "Complete Forme". It has much much better stats. There were theories that this was a fusion with Xernas/Yveltal \(6th generation mascots\) considering it adds blue and red colors and not just green.
  * They gave somewhat importance to this Pokemon, but at the same time it's just a side-quest, it's just something to fill the content that would probably be better to be implemented in the 6th generation, even characters from the 6th generation are the ones that will tell you about the cells and cores of this pokemon.
  * You have to assemble/disassemble Zygardes if you want to get different forms. 
  * Collect cells during your adventure
  * Core and cells are "other forms", but they won't be considered for the games.
  * Oricorio. 4 Forms. These are called styles, the fantasy is that depending on the dance style, the pokemon changes its appearance. Different designs and types. You can change the style by using a flower nectar. It's signature move type changes depending on the style.
  * Lycanroc. 3 Forms. When Rockruff evolves into Lycanroc depending on the version you have \(and also the ability...\).
    * Midday Form. Only in the Sun versions and during the day.
    * Midnight Form. Only in Moon versions and during the night.
    * Dusk Form. Between 5pm and 5:59 pm. Additionally it must have the Own Tempo ability.
      * Own tempo Rockruffs were only obtained via event. \(You can breed them, thought\)
      * It's only available in the Ultra Versions.
    * Different design, stats.
  * Wishiwashi. 2 forms. While in-game they are technically 2 forms. In a Fantasy point of view, it's a bunch of Wishiwashis schooling, and remember, there's strength in Unity. To be able to use a "School Form", Wishiwashi must be at least level 20 and it will automatically change form at the beggining of the battle. It will return to be a single Wishiwashi when it has less than 25% health, this form is called "Solo Form".
  * Silvally. 18 skins. Extremely identical to Arceus, it was based in Arceus. Instead of using "plates" this Pokemon uses "memories". Like Arceus if you change the memory, it will change forms and this is only a re-color.
  * Minior. 2 Forms but one of those forms has 7 different skins. When Minior is above 50% health it will be in "Shell Form", it will change to "Core Form" below 50%. Core Forms skins can not be changed, the Minior you find will always have that skin. Every core skin is based in the Rainbow, that's why there are 7 colors. Forms have different stats and designs, as mentioned before, skins are not a redesign, but a recolor.
  * Necrozma. 4 Forms. Based in Kyurem. There's a "normal" Necrozma. Like the DNA Splicers, this Pokemon will fuse with a Solgaleo or Lunala, you will lose your Solgaleo/Lunala but you can recover it if you unfuse them. Sadly, Necrozma needs 2 different items to fuse, instead of one \(like Kyurem\). 
    * Lunala fusion using the N-Lunarizer to get Dawn Wings Necrozma
    * Solgaleo fusion using the N-Solarizer to get Dusk Mane Necrozma
    * The third form is called "Ultra Necrozma", but the gimmick here its that it needs to be transformed in either "Dusk Mane" or "Dusk Wings". Make it hold the "Ultranecrozium Z" and then use the move "Ultra Burst" in the Battle screen and it will transform. It works like a Mega Evolution or Primal Reversion.
* \[UPDATED\] Pokemon rebalaced stats
  * 26 Pokemon have their stats rebalanced
* \[UPDATED\] Pokemon Events
  * Alolan Exeggutor
  * Guardian Deities
    * Tapu Koko
    * Tapu Lele
    * Tapu Bulu
    * Tapu Fini
  * Cosmog
  * Solgaleo \[SUN ONLY\]
  * Lunala \[MOON ONLY\]
  * Necrozma
  * Sandygast
  * Ultra Beasts
    * Ultra Beasts are just roaming an specific area and don't have an overworld sprite in the Normal Versions
    * Ultra Beasts have an Overworld Model in the Ultra Versions. This just gives me the feeling of how lazy and unethical this feels.
      * Nihilego
      * Buzzwole \[SUN ONLY\]
      * Pheromosa \[MOON ONLY\]
      * Xurkitree
      * Kartana \[SUN ONLY\]
      * Celesteela \[MOON ONLY\]
      * Blacephalon \[ULTRA SUN ONLY\]
        * Doesn't have an Overworld model for some inconsistent game-design reason.
      * Stakataka \[ULTRA MOON ONLY\]
        * Doesn't have an Overworld model for some inconsistent game-design reason.
* \[IMPORTANT\] Only some Mega-stones were added at Launch and can be obtainable in the game.
  * While it's true that Mega-evolution is not what this game is about, it's fair to add these items, since they are part of the Pokemon legacy.
  * Some Mega stones were distributed via Mistery Gift. This is an issue as new players won't have any way to get the missing Mega evolution stones.
    * Limited Time Download Code Mega Stones \(Unobtainable today in Sun/Moon\)
      * Beedrillite
      * Pidgeotite
      * Mewtwonite X
      * Mewtwonite Y
      * Ampharosite
      * Steelixite
      * Heracronite
      * Houndoominite
      * Tyranitarite
      * Sceptilite
      * Blazikenite
      * Swampertite
      * Gardevoirite
      * Mawilite
      * Aggronite
      * Medichamite
      * Cameruptite
      * Manectite
      * Altarianite
      * Banettite
      * Latiasite
      * Latiosite
      * Audinite
      * Lopunnite
      * Abomasite
      * Galladite
      * Diancite
    * However if you pay for the Ultra Versions, you can beat the game and obtain all the previous mega stones with battle points. Is this fair to the players? If they are really concerned about kids, is this really something simple for kids?
* Complete 3D Movement, you don't move in a grid anymore.
* \[UPDATED\] Bag
  * Once again, every generation Game Freaks decides to not stick to something and revamp the bag. These are the pockets for the 7th generation.
  * Medicine
  * Items
    * Pokeballs
      * Apricorn balls are back, after many generations. They are VERY VERY LIMITED.
  * TMs \(Remember that HM were removed from the game\)
  * Berries
  * Key Items
  * Free Space \(Well, at least this is back!\)
  * Z-Crystals \(Why didn't we get a bag for Mega-stones?\)
  * Rotom Powers \[Ultra Versions Only\]
    * \[REMOVED\] O-Powers
* \[UPDATED\] Battle changes
  * \[REMOVED\] Triple Battles \(Yup, got rid of a whole format\)
  * \[REMOVED\] Rotation Battless 
  * \[REMOVED\] Horde Battles
  * You can see your trainer at battle, a feature that was introduced in Pokemon Colosseum for the Gamecube, remember that we are not talking about those.
  * Added Battle Styles
    * Each Battle style changes this
      * You can change your trainer pose on the Vs. Screen
      * You can change the way your trainer throws Pokeballs when sending out Pokemon.
  * Added Z-Moves
    * Make a Pokemon Hold a Z-Crystal and it will be able to attack with
  * Added S.O.S Battles
    * Some Pokemon can call for help and another Pokemon will join. Essentialy making a 1v2 battle.
    * \[REMOVED\] Dex Nav/PokeRadar
      * S.O.S are the new "chaining" feature for non-fishing encounters.
    * Pokemon can keep calling for help and it also slowly increases your chances to find Shiny Pokemon.
  * Battle Screen
    * \[IMPORTANT\] There's an exclusive button \(and button\) for you to select a Pokeball. 
  * \[DEBATABLE\] Fight Screen
    * When selecting moves, if you've seen the Pokemon you are battling with, the moves will tell you how effective they are against the enemy Pokemon. This aid can be unexcusable to many pokemon veterans, considering how veterans had to learn the type matchup by themselves, now there's no need to even think, since the game will remind you the effectiveness.
  * You can see how much your stats have changed if you tap your Pokemon Icon. 
  * You can see how much the enemy pokemon stats have changed as well.
    * Eg. If you use Sword Dance, you can see it was raised 2 stages
    * You can see your Pokemon's Ability, but not the enemy.
    * You can see what item your Pokemon is holding
    * You can see your Pokemon's types.
* \[UPDATED\] PC Storage System
  * Total Boxes: 31
  * Total Capacity: 960
* Added "Pokedex Quests"
  * You will find some people that want to see a specific Pokemon. An incentive to capture that Pokemon and show it.
  * \[IMPORTANT\] There's no need to add the Pokemon to your party.
* \[REMOVED\] Fish anywhere you want
  * Added Fishing spots
    * This places have their own pool of Pokemon per spot.
  * \[REMOVED\] Old Rod
  * \[REMOVED\] Good Rod
  * \[REMVED\] Super Rod
  * Added Fishing Rod
    * There's now only one fishing rod. This is good and bad, probably another mechanic would be to change and experiment with different kinds of lures to find specific kinds of Pokemon that like certain lures to increase and decrease changes. Overall, its more good than bad.
* \[REMOVED\] Battle Maison
  * \[EQUIVALENT\] Added Battle Tree
    * The gimmick here is the fact that Red and Blue \(and other generation important NPCs\) were the bosses at the Battle Tree with a new design.
    * Less content, due to removal of Triple Battles
    * Less content, due to removal of Rotation Battles
    * You can use Rental Pokemon, but as far as I know, Rentals have to be "uploaded" to the Pokemon Global Link, making it something that will probably get deprecated in the future, this is relevant as this is not actually in-game.
    * You can select which battle music you want to play here.
      * Ultra Versions removed music but added other songs.
  * Added the Battle Royal Dome
    * A new battle format called "Battle Royal"
      * It's a 4v4 battle mode. 4 Players send out a Pokemon and the last one standing wins.
    * Reach up to Master Rank
    * You also get Battle Points here
    * There are 51 trainers to face
    * Final Boss is `The Royal`
* \[REMOVED\] Trainer Card
  * \[EQUIVALENT\] Trainer Passport.
    * Just renamed. Here's what you have to do in this game.
    * Complete the Island Challenge
    * Complete the Alola Pokedex
    * Win 50 Consecutive battles in Single Battle's battle tree.
    * Win 50 Consecutive battles in Double Battle's battle tree.
    * Win 50 Consecutive battles in Multi Battle's battle tree.
    * Obtain the Final Version of the Poke Finder
* Added the Poke Finder
  * Probably an upgrade from X/Y Photo Poke spots, this is a very GRINDY game mode. Certain areas of the game allow you to take photos, Pokemon will show up here and your job is to take them photos, probably based on Pokemon Snap. Personally, this feature feels really incomplete.
  * You have to upgrade the Poke Finder to version 5.0 and it will give you an upgrade to your trainer passport.
* \[REMOVED\] PSS
  * Added Festival Plaza
    * Consider it a fusion of the Join Avenue and the Entralink  Missions. The problem here is the fact that Generation 6 set the bar high and this feels like a downgrade. As mentioned in other points, changing features for something more "invasive" is something players don't like. The PSS \(Gen 6\) worked in any area of the game, on the other hand, the Festival Plaza is a place where you have to go, like Entralink \(Gen 5\).
    * Battle Button on the touch screen allows to:
      * Access to Link Battles
      * Visit the Battle Spot
      * Download Battle Rules
        * Use downloaded rules in your Link Battles
    * Trade Button on the touch screen allows to:
      * Have Link trades
      * Access the GTS
      * Make Wonder trade
    * Like Join Avenue, you rank/level up this place.
      * Max Rank is 100
    * Change the plaza music if you reach Rank 40
    * Festival Coins are the currency
    * The Pokemon Global Link is still present.
    * Added Festival Tickets
      * Need tickets in order to host missions.
      * 3 Tickets are handed every day.
    * Missions
      * Host Missions
      * Join Missions
      * Mission Types
        * Break Boulders with Tauros
        * Talk to Visitors with a \[specific condition\]
        * Send Visitors to a specific facility
        * Choose an attack super effective against the proposed from a visitor
      * Global Missions
        * Missions that ALL PLAYERS in the world work to complete. Players will always get Festival Coins
        * Additionally if the player joined the Pokemon Global Link can get extra rewards like \(these depend on the misson\):
          * Rares Candies
          * Apricorn Balls
        * As of today, Global Missions have been deprecated and they were timed limited months before the release of Pokemon Sword and Shield.
    * Facilities \(Very similar to Join Avenue\)
      * Lottery Shops \(The old lotto ID mechanic\)
      * Bouncy Houses
        * EV training
      * Haunted Houses
        * Send a Pokemon to pick up a random item from it. You can get VERY RARE items, like bottle caps or even a Sacred Ash. An Item with limited quantity.
      * Food Stalls
        * Meals that can
          * Level up Pokemon multiple levels
          * Increase EVs
          * Decreae EVs
          * Increase Happiness
      * Goody Shops
        * Buy Pokeballs
        * Buy Items
          * You can items from previous generations as well
            * Rage Candy Bar
            * Lava Cookie
            * Old Gateau
            * Casteliacone
            * Shalour Sable
      * Fortune Teller-tents
        * Forewarn and suggest about the "luck' of the various random events in the game. Players can try to test their luck at the suggested location.
      * Dye Houses
        * Dye your trainer customization items \(called Fashion items\)
        * \[DISSAPOINTING\] There are version exclusive colors
          * Like why would you make a color exclusive to a game? What kind of nonsense is this? Why would you constraint this kind of stuff when you didn't do this before? This takes away the real customzation that many players love.
      * Switcheroo \[ULTRA VERSIONS ONLY\]
        * Shuffle rental pokemon for the Battle Agency
      * Battle Agency
        * Similar to the Battle Factory
        * If you defeat more players  you get a better range of Pokemon to use.
        * Players get assigned a Pokemon, this changes every day.
        * There's around 1000 diferent pokemon from the rental pool that trainers could get their hands on \(this is RNG based\)
  * Players you meet at the plaza can have requests, completing them will net you Festival Coins    
* Added Quick Link
  * A slower way to communicate locally. The PSS was faster and you just had to tap the player you wanted to connect with.
  * This is now an option of the Player's menu.
  * This feature looks for player who are tapping the touch screen and matches them to access wireless activities.
* New Evolution methods
  * Version exclusive evolution \(Cosmoem to Solgaleo/Lunala\)
* Dungeons ~ Total: 16  \(13 if we consider Ruins as one "big" dungeon\)
  * Alola is a very weird case. Since they are Islands, this place has more open areas. But I'm sticking to consider dungeons as I considered them in previous generations. Routes are not considered dungeons. But keep in mind that routes have places to use your Ride Pokemon, just a heads up, many routes here are semi-dungeons. The quality of dungeons dropped considerably in this generation.
  * Malie Garden is an honorable mention, but a dungeon.
  * Ultra "areas" will not be considered a dungeons.
  * While there are 4 ruins, they are just a room with 1 puzzle, I will consider them as a dungeon, although pretty much the 4 of them could be considered as 1.
    * Aether Paradise 
    * Digglet's Tunnel
    * Haina Desert \(While an Open Area, this place is a maze\)
    * Lush Jungle \(Part of trial, but still dungeon\)
    * Mount Lanakila \(Alola's Victory Road\)
    * Po Town \(I would consider a special case. It's more or less a dungeon\)
    * Resolution Cave
    * Ruins of Abundance
    * Ruins of Conflict
    * Ruins of Life
    * Ruins of Hope
    * Sandy Cave
    * Seaward Cave
    * Shady House
    * Team Rocket's Castle
    * Ten Carat Hill \(Incredibly linear\)
* \[REMOVED\] Pokemon Amie
  * \[EQUIVALENT\] Added Pokemon Refresh
    * \[REMOVED\] Mini-games
    * Pokemon have specific areas where they they like to be pet.
    * There are Pokemon that can get hurt when you pet certain spots.
    * Still using Affection, Fullness, Enjoyment
    * Affection will be lost if you trade the Pokemon BUT you don't trade it back the same day.
    * You can feed Pokebeans
    * After a battle ends, you can use certain "refresh" items to heal them from status ailments.
    * Yu get the same Affection benefits like in Pokemon Amie
* Added QR Scanner
  * You can scan a code to mark as a Pokemon as "seen".
  * Rare and Legendary Pokemon don't have a QR Code.
  * You could get a Magearna is you scanned its special QR Code. You know, another special way of getting limited edition Pokemon.
  * Island Scan
    * You earn points for Scanning QR Codes. By using 100 Points you can use the Island Scan.
    * The Pokemon change every day, each Pokemon appear only at a certain day.
    * You can even find starter pokemon from other regions here.
* \[REMOVED\] Super Training
* \[REMOVED\] Berry harvesting
  * There's an Area in the game called "Berry Fields" and guess what, you can't grow berries here. Why would you even bother making this area?
  * Added Poke Pelago
    * Use of the Pokemon from your boxes
    * The objective is to collect Poke Beans. \(Yet another Poke thing, like the Pokeblocks, Puffins, etc\)
    * You have to fully develop 5 Islands and each Island awards you different things.
    * You rank up the Islands as you get more Pokemon in your boxes. You will need around 90 Pokemon in yor boxes \(3 Full Boxes\)
      * Isle Abeens
        * Gather Pokebeans in here
        * Attract Wild Pokemon, their rarity and level depends on your progress of the game.
          * There's a pool of Pokemon that can show up here
      * Isle Aplenny
        * This is where you grow berries, this can be considered the improvement of the Berry Pots, because you can launch the Poke Pelago anywhere you are.
        * It takes from 1 day to 3 days for berries to grow.
        * Pokebeans can help berries grow faster
      * Isle Aphun
        * Send Pokemon to missions, they will be able to collect special items, like evolution stones, shards, treasures.
      * Isle Evelup
        * Place up to 6 Pokemon to EV Train them with various drinks.
        * You can also train then for Exp. Points
        * Sessions last 30 minutes.
        * At max isle rank, you need 63 sessions to max out a stat. 63 sessions = ~31 hours.
        * Pokebeans can make sessions last 15 minutes.
      * Isle Avue
        * Place Pokemon here to increase their happiness.
        * You can place eggs here to hatch them.
        * Using Pokebeans will double Pokemon's happiness.
        * Using Pokebeans will make eggs hatch faster
* Added Berry Trees to collect berries in the map
  * Second time Game Freak gets rid of this overworld harveting.
* Rival
  * Hau a very very friendly rival
  * Gladion, non-friendly at first, neutral at the end.
* \[UPDATED\] Time Mechanics
  * In the Moon versions time is 12 hours away from the Sun versions. If still confusing, when in the real world is daytime, the Moon versions will be at night.
* Added The Alternate World
  * You can enter the alternate world with a Solgaleo or a Lunala.
  * When you enter, you can consider that you pretty much "entered" the other version, except that you won't get any exclusive version Pokemon, but there's a loophole here
  * You can get a Cosmog and trade it to the other version and evolve it there, so you can trade back your Cosmog as the legendary mascot of the other game.
* \[IMPORTANT\] Added Hyper training
  * In past games, you could never modify pokemon's genes. Hyper training allows you to maximize IVs
  * If you breed a Pokemon with modified genes, it won't pass the genes.
  * You can only hyper-train Pokemon if they reached Level 100.
  * Added two bottlecaps
    * Bottle Cap
      * Raise one IV to max
    * Gold Bottle Cap
      * Raise all 6 IVs to max
* \[REMOVED\] Gym leader rematches \(Here they are called Trial Captains\)
  * A new generation, another old feature cut.
  * You can fight the Fire Captain at the battle tree in the Sun Version
  * You can fight the Grass Captain at the battle tree in the Moon Version
* Added Mantine Surf \[ULTRA VERSIONS ONLY\]
  * You can get Battle Points here, if I haven't messed things up to this point. This is the first time you can get Battle Points in a Non-Battle activity.
* Move Tutors
  * Same trend. Special Versions are the only ones who have the better and real move tutors. You can see a pay-to-win situation for players who only get the first versions.
* Travel to the Ultra Space \[ULTRA VERSIONS ONLY\]
  * You can find many other pokemon here.
  * You can also evolve alolan pokemon to their Kanto forms in here.
  * You can find many Legendary Pokemon in this place.
* \[REMOVED\]  Champion NPC
  * This is the first time there's no champion in a Pokemon game, but it's well justified, since in this game it's the first time they have a Pokemon League, when you win the final challenges, Professor Kukui will tell you that you are now the first Champion of Alola and that now you have to defend your Title, so this time people will come against you, just like Red defeated Blue in the first game taking his Championship very quickly.
* \[UPDATED\] NPC Judge
  * \[IMPORTANT\] After hatching 21 Eggs, you can consult the judge at the PC. It will have this range of messages. It's a great upgrade. According to bulbapedia:
    * IV of 0: "No Good"
    * IV range of 1-15: "Decent"
    * IV range of 16-25: "Pretty Good"
    * IV range 26-29: "Very Good"
    * IV of 30: "Fantastic"
    * IV of 31: "Best"
* Updates
  * Pokemon Sun/Moon were updated to version 1.2
* Post game
  * Episode Rainbow Rocket \[ULTRA VERSIONS ONLY\]
    * A post-game small story that unites all previous generation teams. Rainbow because 7 colors, and well, 7 evil Teams.
    * As a note, Team Skull is not the evil team, it's the Aether Foundation.
  * Collect all Z-Crystals
  * Get all the Trainer Passport stamps
  * Side Quests \[ULTRA VERSIONS ONLY\]
    * Serebii lists 35 sidequests in the game.
* This is probably the special versions that seem to add less content to the games. The inclusion of "more story" is something you have to expect and that is a must because... well, they are selling another product. So, overall its even more dissapointing considering how the Hoenn Remakes expanded more things, and how Pokemon Black/White 2 were actual sequels and nost just a re-skinned version of the game. If players already thought that it's unethical to sell the special versions, the ultra versions really shout out how they had to be the original versions of the generation, and probably make a sequel of them, not only that, this is the first time there are 2 Special Upgrade versions, as BW2 are sequels.

[Return to Navigation](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#quick-navigation)

## Generation VIII

Nintendo Switch: 2019

With the previous stated categories, this marks the beginning of the Bronze Age of Pokemon. Pokemon now moved to the Home Consoles and with it, we can expect that since the games are going to cost 60 dollars, we will expect great features now, since they have our financial support. Check out how just how many things were removed. Comparing the previous efforts from game freak, we can say that _this is not a 60 dollar game_, it feels unethical.

* Improved 3D Graphics, although they are still worse than much of the flagship graphical Switch games. But they are still the best Pokemon graphics ever.
* \[REMOVED\] Mantine Surf
* \[UPDATED\] Gym Leader rematches
  * Rematches are back, but in a very different way. Since the game's story goes around the Gym Challenge, Gym leaders can only be rematched at the Champion Cup. 
  * You can invite a Gym Leader to join the Champion Cup. Essentially you are defending your Champion Title when you get the capacity to have rematches.
  * The invited Gym Leader will be at the Champion Bracket, so far you will always fight this trainer.
  * The downside here is that you have to enter the Champion Cup and lose a lot of time, to fight the Gym Leader you want to rematch, instead of just going to a location where you could rematch Gym leaders, like in the Fourth generation. This is similar to the Pokemon Global Championship. But hey, better have it this way that not have it this way.
  * The battle music here IS NOT THE GYM LEADER THEME, another way to see it, its that this Music could be the Elite 4 Music, since it's the Champion Cup \(even if there's no elite 4\)
* \[UPDATED\] Champion NPC is back, his name is Leon
* \[REMOVED\] Elite 4
* Move tutors
  * Still missing the cool tutors.
  * \[REMOVED\] Many tutors for Pokemon like Keldeo, Meloetta, since they were removed from the games.
* \[UPDATED\] Move reminder
  * Can now teach Egg moves, if your Pokemon had that when born.
* \[UPDATED\] The Pokemon Center
  * Left: Pokemon Services
    * Name Rater
    * \[UPDATED/IMPORTANT\] Move Reminder
      * No longer need to pay with a Heart Scale.
  * Mid: Nurse
  * Right: Pokemart
* \[UPDATED/IMPORTANT\] IV Judge
  * \[REMOVED\] NPC Judge Character
  * Now you can unlock the "Judge" in your Pokemon Boxes, you can check IVs anywhere you want. You unlock this by ranking up to the Poke Ball Rank in the Battle Tower.
* \[UPDATED/IMPORTANT\] Pokedex
  * They took more than they take
  * 80 New Pokemon species
  * Galar Forms \[INSERT NUMBER HERE\]
  * Added Gigantamax Forms
    * Gigantamax Pokemon have a unique move for that specific species.
  * \[IMPORTANT/UPDATED\] There's only 400 Pokemon available as playable Pokemon in this game.
    * \[REMOVED\] 490 Pokemon. Completely removed, you can't even transfer them.
      * If a Pokemon had a form, those were removed as well, as expected. \(Eg. Deoxys, Pyroar\)
      * HUGE WARNING. You can't transfer Pokemon that are not in the Galar Pokedex. You can't transfer a Cyndaquil at all. 
      * [List of Unobtainable and Untransferable Pokemon](https://www.serebii.net/swordshield/unobtainable.shtml)
      * A big issue with the Pokemon being removed is that this goes against one of the goals of every single game.
        * Create a Bond with your Pokemon and become great Partners
        * The Pokemon's motto: "Gotta Catch'em All". Even in the previous generation that removed the National Dex as a "Pokedex Mode", you could even find and catch Pokemon that were not in the Alolan Pokedex. Which is quite a huge problem because the players can't keep track of those Pokemon, because the game is was not listing them, the only way to list all your 809 Pokemon \(as of Gen 7\), was to Buy the Pokemon Bank Membership, that's right, you had to pay more money to use AN EXTERNAL APP to track your progress, when explicitly Pokemon Gold/Silver tracked everything for you too.
  * \[REMOVED\] Mega Evolutions and Primal Reversion
  * \[REMOVED\] Roto Loto Powers
  * \[REMOVED\] Pokedex Quests.
    * Although the "pokedex quests" were removed, the pokedex now suggests Pokemon to catch.
    * According to Serebii, the "recommended" Pokemon have higher chances to appear. Making it the equivalent of "Swarms" in this generation.
  * Pokedex gives suggestions of what you can catch
  * \[IMPORTANT\] Added Sort Mode.
    * Reverted to Generation 3, it was called "Order Option" in that generation. 5 steps back.
  * \[REMOVED\] Search Mode.
    * There's no way to enlist your missing Pokemon
    * No way to list Regional Forms, or Shiny Forms as a separate list. This is a huge step back
  * \[UPDATED\] Habitat In-Depth search.
    * \[REMOVED\] In-Depth Habitat for Routes. There's no minimap anymore, so, you can't use it.
    * The closest thing you will see is the fact that Pokemon that appear in the Wild area show the zone where they appear.
* \[UPDATED\] Pokemon fossils
  * For these games, you are creating fusions of fossils, they seem like abominations but at least it's fresh content.
* New Evolution Methods
  * A new and interesting evolution method has been added. You need to attach a Sweet to Milcery and then spin your character by rotating the control stick.
    * Milcery's evolution, Alcremie has 63 forms \(skins\), but there's only 7 Shiny versions, making in total of 70 different Alcremies essentially making the Pokemon with most forms to date, plus one more Gigantamax form.
    * There are 2 missing Sweats at launch. Star and Ribbon sweats are no where to be seen. So at launch, there's only 46 forms available, and missing 18. Once again Game Freak has all this content at launch, instead of actually adding it after launch via online updates.
* \[REMOVED\] Mini Map on Touch Screen
  * Without a second screen, it was expected to see something like this. Still many games include a small minimap on the screen with some transparency. Navigation in Alola was the best navigation we had. In this game you have to interrupt your gameplay to see the map.
* \[UPDATED\] Battles
  * \[UPDATED\] Moves
    * \[REMOVED\] For the first time ever, with the removal of more than half of the Pokemon, many moves were also removed from the game.
      * Around 144 Moves were removed.
    * \[REMOVED\] Z-MOVES
  * \[UPDATED\] The Battle Screen has been revamped to only use 1 screen, instead of 2.
  * \[REMOVED\] S.O.S Battles
  * \[REMOVED\] Battle Styles
* \[REMOVED\] The Alternate World
* Added the Wild Area
  * This is a huge area in the game that can pretty much be considered AN INMENSE ROUTE. It can also be considered an INMENSE Safari Zone. 
  * It is a great addition to the game, as there are many zones in this big area, plus you can find many evolved Pokemon, in the overworld here. You are also going to find Pokemon of higher levels as you progress your adventure.
  * Each day the weather changes and with it, different Pokemon will appear in each zone of the Wild Area.
  * Added Raid Dens
    * Interacting with a "energized" den will award you Watts, this is the main way of getting Watts. Your Pokedex will tell you in which weather a Pokemon can appear
    * Each den have a 2 pools of available Pokemon.
      * Common Pool / Common Den
      * Rare Pool / Rare Den
        * This is the only pool where you can find Gigantamax Pokemon
  * Added a Weather system for the different zones in the wild area.
* Added New forms
  * Alcremie has 63 forms \(skins\).
  * Cramorant has a "form" which is essentially just this Pokemon's ability in battle. It has small similarities with Wishiwashi's since depending of health it will change. But this forms actually goes into the same category as Aegislash.
    * Gulping Form
    * Gorging Form \(this one is so funny\)
  * Sinistea. Just a small and great detail regarding porcelain.
    * Forgery Form
    * Authentic Form
  * Eiscue. Very similar to Mimikyu's but when changes form, it's stats change.
  * Indeedee. A gender form. They have different stas.
  * Morpeko.
    * More than a form, this is calleed "Mode". But it's pretty much the same. The only difference is the fact that if Morpeko uses the move "Aura Wheel" it will have a different type, alternating between Electric or Dark type. 
    * Same form category as Aegislash.
  * Zacian
    * Hero of Many Battles Form
    * Crowned Sword
      * If you make it hold the Rusted Sword
      * Types change
      * Stats change
  * Zamazenta
    * Hero of Many Battles
    * Crowned Sword \(I guess this is Crowned Shield?\)
      * If you make it hold the Rusted Shield.
      * Types change
      * Stats change
  * Every Pokemon can Dynamax \(Except Zacian and Zamazenta\)
    * But... this is just scaling the models, so they don't really count. Besides, Pokemon only change their max HP.
  * With the Dynamaxing, there's also a new mechanic which is called Gigantamaxing. Think of a fusion of Mega-evolution with Z-Moves. 
  * Pokemon with Gigantamax available at launch.
    * Charizard
    * Butterfree
    * Machamp
    * Gengar
    * Kingler
    * Lapras
    * Garbodor
    * Corviknight
    * Orbeetle
    * Drednaw
    * Coalossal
    * Flapple
    * Sandaconda
    * Centiskorch
    * Hatterene
    * Grimmsnarl
    * Alcremie
    * Copperajah
    * Duraludon
  * Special cases Gigantamaxs
    * Pikachu
      * Can only obtain it if you have a save file of Pokemon Let's Go Pikachu on your Nintendo Switch. For the average consumer, this is a $60 dollar Pokemon. Yes, you can ask someone to burrow their games, and players will just create a save file to unlock this Pokemon, it's not practical.
    * Meowth
      * Limited time event in Mistery Gift. Expected to end distribution in early 2020.
    * Eevee
      * Same as Pikachu, but with Let's Go Eevee
    * Snorlax
      * Not available at launch, but became available with an Online Update, making it available to appear and catch at dens, during the time of this writing this document it is unknown if it will stop appearing after January.
    * Melmetal
      * Unobtainable at launch by no legal means at the time of writing this document. \(Game manipulation doesn't count\)
    * Toxtricity
      * Unobtainable at launch by no legal means at the time of writing this document.
    * Eternatus
      * While it has a Gigantamax form, once you capture this Pokemon, you can't access to its Gigantamax form, this is the first time we see this kind of "Pokemon Boss" do that.
* \[UPDATED\] Bag. Here's a list of the new pockets for the game, because for the 8th time, Game freak keeps changing this.
  * Medicine
  * Poke Balls
  * Battle Items
  * Berries
  * Added Other Items
    * Repels
    * Held Items
    * Evolution Items
    * Vitamins
    * Candies
      * Added Dynamax Candy \(Another pointless item, this item raises a pokemon's "dynamax level". \)
      * Added Exp. Candies from XS to XL Sizes
  * TMs
    * Added TRs ~ Technical Records
      * As you remember, from generation 1-4, TMs could only be used once. Well, in this game they added them back with the name of "TR". You can keep getting this items, they are not missable/non-renewable, so it's pretty much pointless to have them in the game, given how generation 5 improved this so much.
      * In some Raid Battles certain TRs drops are version exclusive. But still every TR is any version of the game.
  * Treasures
    * Items like Nuggets, Pearls, etc
    * Fossils are here
    * Bottlecaps are located in this pocket, I think this is a misdirection for unexperienced players, what if those players sell the Bottlecaps accidentally, bottle caps are very useful and rare items.
  * Ingredients
    * With the addition of Pokemon Camp, these are items used to create curry. 
    * Expect a high chance to be removed in the next generation.
  * Key Items
    * \[UPDATED\] Escape Rope is now a key item.
      * And why would you want an Escape rope, if the dungeons in this game are pretty much empty and they are not even mazes? They don't even have multiple floors.
* \[UPDATED\] Pokemon Events
  * Zacian \[SWORD ONLY CATCH\]
    * Story
      * Appears with Zamazenta for the story event to defeat Eternatus
    * Post Story
      * You fight him first in Shield, and then leaves so Hop can capture it.
      * You fight him last in Sword, you can capture it in this battle.
  * Zamazenta \[SWITCH ONLY CATCH\]
    * Story
      * Appears with Zacian for the story event to defeat Eternatus
    * Post Story
      * You fight him first in Sword, and then leaves so Hop can capture it.
      * You fight him last in Shield, you can capture it in this battle.
  * Eternatus
    * Appears as a Dynamaxed Pokemon Boss
  * That's it, nothing more, there's no more lore or any other Pokemon that fits the adventure.
* Added Exclusive Gym Leaders, again.
  * Last time we different content in versions regarding of story was in Pokemon BW, with Drayden and Iris, but they also added the Black City and White Forest. This game only adds different gym leaders
  * Sword exclusive
    * Fighting Leader ~ Bea
    * Rock Leader ~ Gordie
  * Shield
    * Ghost Leader ~ Allister
    * Ice Leader ~ Melony
* \[UPDATED\] Rival
  * In this game you have three rivals.
    * Hau the friendly rival.
    * Bede a non-friendly rival. 
    * Marnie the neutral rival.
* \[UPDATED\] Villian Team
  * Just as stated in Early trailers of the game. Team Yell is not an evil team, they are just some random dudes who will be a bad game design to block your path in the game's routes. They will literally just be a hitbox that will stop you from going to another area in the game. This is coming from a non-narrative point of view. Personally I think that adding the "Team" in their names is what can also segregate Pokemon fans, as the "Team \[something\]" 
  * The "real bad guys" are Macro Cosmos, much like the previous version was Aether Foundation. And while many Pokemon veterans will know that Rose is the bad guy just by looking the first cutscene of the game, you will only have 2 battle encounters with this "evil team", and it feels like a huge waste of time because it's only 1 encounter that feels forced because there has to exist conflict in the game.
    * 1 Encounter to defeat some employees and Oleana.
    * 1 Encounter to defeat Rose
    * Serebii lists 13 encounteres but only 2 are battle encounters, older generations made much better than this, specially gen 4 and gen 5.
* Rebalancing stats
  * Only 1 Pokemon got a rebalance on their stats and it was a nerf. This pokemon was Aegislash in both of their forms.
* \[IMPORTANT\] Added Max Raid Battles
  * This is a brand new PvE content for the game. You can team up with up to 4 players to fight a Dynamaxed Pokemon. It's a 4v1 battle. 
  * All players get a chance to catch this Pokemon. Here's another reminder of how a feature can have its own depth and we the idea is to not go super in-depth. But there are people trying to figure it out things like Catch rates and how Hosts of the Raids always have 100% and stuff like that, just a heads up of how people have been experimenting with this.
  * Sadly, these bosses are just Sponges. Pokemon's battle system is easy, and it's pretty much your fault if you bring a Pokemon that is weak versus the Raid Pokemon Boss. You could in theory one shot this Pokemon, but they suddenly generate "shields" for you to elongate the fight. It's very time consuming, there are even moves that do more damage to Dynamaxed Pokemon. Even if you do only 1 damage it will take a shield down, these battles are just something that take too much time and they are no different than a normal Pokemon fight. The only good thing \(and it's a great thing\) is the fact that this is a Multiplayer feature, the social aspect of this feature is what makes it bearable, there is a lot of room for improvement.
* \[REMOVED\] Ride Pokemon
  * With the removal of Ride Pokemon, they have removed 95% of all non-linear exploration.
    * There's not much exploration in this game, they wanted to put their efforts on the "Wild Area", but it's just a huge Route. It gets repetitive as the real novelty is the fact that it's "an even more 3D area" than the routes and caves in this game. Plus, with the Wild Pokemon showing in the overworld, you can literally just go to the beginning and end of route in SECONDS. This makes it the most straight-forward core pokemon game ever.
  * \[UPDATED\] Bike
    * Your phone is now your Bike, since your Phone is a Rotom. If you don't know, part of the lore is that Rotoms can get into any machine, your phone being one.
    * Now has a turbo mode to even move fasterr
    * Now can go through water. No Pokemon are needed to use Surf or equivalent. This is the only thing that would make you go back to other areas, to "see what you missed because there was water on your path, but you didn't have the bike".
* \[REMOVED\] Dowsing Machine
  * Completely removed. If you want to find Hidden items in the game, well, they are not really hidden, you can see on the ground with sparkly effects, those are the "Hidden" items. They even got rid another micro-exploring mechanic.
* \[REMOVED\] Z-Trainers
* \[MISSING\] Berry Harvesting
  * In this game, like the previous one \(ignoring Poke Pelago\), you get berries at berry trees, they reset daily. The new gimmick is that you can keep shaking the tree to get more berries, but the more shakes, it more probable for a Pokemon to steal your berries.
* \[REMOVED\] Poke Pelago
  * \[EQUIVALENT\] Added Poke Jobs. A somewhat equivalent. It is an improved Evelup Isle from Alola's Poke Pelago.
    * Just like Evelup Island, you send Pokemon for real time. 
      * 1 Hour
      * Up to 24 hours
    * You can send Pokemon get items. It's easier to get items in other way, rather than using the Poke Jobs, it's better to use it for EV training.
    * You can send Pokemon to train their EVs
* \[UPDATED\] Wild Encounters
  * This is the first core game that makes Pokemon appear in the Overworld.
  * There are still random encounters, and these "random bush" encounters can make rare pokemon to show. Not all Pokemon appear in the Overworld
  * Added Brilliant Aura Pokemon
    * With Pokemon showing up in the Overworld, you will see Pokemon with a "brilliant aura".
      * Defeating or catching will award you Watts
      * These Pokemon can have egg moves.
* \[UPDATED/IMPORTANT\] Vitamins
  * For the first time, you can use 26 Vitamins to increase Pokemon's EVs. Remember, you could only use 10 Vitamins per stat, adding 100 EVs in one stat. This is a great change.
* \[REMOVED\] Pokemon Refresh
  * \[EQUIVALENT\] Pokemon Camp
    * Almost identical to Amie and Refresh, since pokemon have the same benefits if you have better friendship. 
    * \[UPDATED\] Happiness
      * Your Pokemon can no longer max out their happiness outside of Pokemon camp. In these games Affection and Friendship are tighly coupled, if you want to maximize your happiness you have to play with your Pokemon in Pokemon Camp. This is a very weird addition to the game, but it makes sense in a narrative way, but probably they should've stick to what they had before.
    * Added Curry Cooking.
      * Added a Curry Dex
      * There are 151 different curry.
      * 6 different taste ratings.
    * Added Simple color customization for your tent
    * You can visit other player's camps.
* \[REMOVED\] QR Scanner
* \[REMOVED\] Quick Link
* \[REMOVED\] Festival Plaza
  * \[EQUIVALENT\] Y-Comm
    * The next iteration of the PSS and Festival Plaza. Sadly, with the removal of a Second Screen this obviously had to be a worse iteration, because of how quick and immediate the PSS was to use.
    * On the Overworld you can see the various cards from other players and their activities.
    * If you press the Y button \(Y-Comm! 😲\) the Y-Comm screen will show.
      * To the right "cards" will show up, these cards will tell you what other trainer are looking to do. 
        * But here's the downside. These cards are just information, they don't do anything else, you can'y interact with other player's cards. 
        * The only card you can interact with is when a player is seeking for more players to do a Max Raid. The UI is not coherent as it can "fool" other users making them think that they can interact with those cards.
        * There are more UnInteractive cards THAN Interactive cards. UI wise this doesn't make sense.
      * You can put "Link Codes" in your activities. Link Codes are specially useful if you are in a real life crowded area.
      * Select Features on your left side of the screen
        * Link Battles
        * Link Battles
        * Renamed Wonder Trade to Surprise Trade
        * Trade League Cards with other players
        * Profile
          * If you recall, the games had Multiplayer avatars. This is how you customize your PvP stuff too.
        * Search Cards
          * You can filter which cards you want to appear on the mid/right side of the screen.
    * So the bad thing is that this could have been as good as the PSS system. You can't see your friends here, and Link Codes are totally unnecesary considering how every player can have a unique ID, then use that ID to match players to the various activities. The fact that "searching..." takes too long with the Pokemon game that has more resources available it's unnaceptable, Game Freak has done better \(still, much better than Festival Plaza\).
* \[REMOVED\] GTS
  * Suprised? I was surprised as well.
* Added Birthday events
  * The game celebrates your birthday \(don't worry they are not tracking your personal data\) with 2 events
    * At the Pokemon Center with a special animation
    * Curry you make on your birthday will have a candle on it.
* Added Pokemon Marks
  * These Marks give Titles to the Pokemon when they go out in battle. Small detail and appreciated it.
* \[REMOVED\] Poke Finder
* \[REMOVED\] Battle Tree
  * \[EQUIVALENT\] Battle Tower
    * The battle tower comes again, and it feels downgraded with formats, as even now yet another format has been removed for this facility.
    * \[REMOVED\] Multi Battles
    * No need to save to enter the battles
    * Any Pokemon can enter the battle tower, even the legendaries.
    * Use of In-Game rental pokemon.
* \[REMOVED\] Battle Royal Dome
* \[UPDATED\] Trainer Passport has been renamed again to League Card
  * You can share your link card with a code.
  * Your league card is customizable.
    * Background
    * Effects
    * Frames
      * There are league card frames only obtainable if you have a save file from Let's Go Pikachu, Eevee and Pokemon Quest.
    * Expression. You can add your trainer's facial expression here.
    * Pose. Your trainer's pose in your card.
    * Foil
  * The league card also shows the following
    * Number of curries made
    * Rally Best Score
    * Number of Pokemon Caught
    * Number of Shiny Pokemon found
  * Other NPC Story related trainers have Trainer cards. This makes a lot of sense, becausse the "sport/football" theme of the game fits these "collectible" cards.
* Added Rotom Rally
  * A minigame to play with your Bike.
* \[REMOVED\] Battle Spot
  * \[EQUIVALENT\] Victory Station
    * The nicest thing is that this in on the main menu.
    * You can use Rental Pokemon Online, you can even use Rental Pokemon in Ranked Matches.
* \[UPDATED\] Mystery Gift is now selectable throught the Main Menu.
* \[IMPORTANT\] Added Nature Altering
  * This is a huge improvement for natures, instead of players keep grinding a nature, they can grind battle points to change their nature with a Mint. Using a Mint will change a Pokemon's nature stats to that Mints's "flavor", BUT IT WILL NOT CHANGE THE NATURE. Just like how bottle caps don't really change IVs for breeding.
* \[UPDATED\] PC Storage System
  * \[IMPORTANT\] For the first time in a core game, you can access your Pokemon boxes ANYWHERE YOU WANT. \(Remember that Let's Go games don't count\). A story event unlocks this for you, it's not missable.
* \[UPDATED\] Breeding
  * You can now pass an egg move to the other parent Pokemon. This is the first time the couple interacts, the Pokemon have to be of the same species.
  * If breeding with Ditto, the other Pokemon can pass the Pokeball the parent has, regardless of the gender. This was only possible for female pokemon.
* Added the Digging Duo
  * A pair of NPCs that if you give them Watts. They will try to find rare items like:
    * Evolution Stones
    * Weather Stones
    * Fossils
    * Treasures
    * Bottlecaps
    * Held Items
    * Wishing Pieces
  * Sadly if feels empty, there's a black screen and no animation to show, this activity is pretty much just generating items from the item pool with their respective chances in a BLACK EMPTY SCREEN.
* Dungeons Total: 4
  * Less dungeons than any Pokemon Game, even Pokemon Red. And even worse, they are a huge lineal thing, they can be considered routes with a different name. There's no floors and since there's no Hidden Moves, there's nothing that blocks your path, except for the Surf Bike.
  * You can see why this is a big issue. Alola had smaller dungeons, but still it kinda wanted to defend itself with the many semi-dungeons on the open areas. The eight generation is the worst generation if you are looking for exploration. Another huge reason to call this the Bronze Age of Pokemon.
    * And there's more routes in Pokemon Red than in this game. This game only has 10 routes. I don't think the Wild Area is covering the exploration sense previous games had. The Wild Area is a Safari Zone.
  * Slumbering Weald
  * Galar Mine
  * Galar Mine 2 \(When they ever add a number to a Dungeon?\)
  * Glimwood Tangle
* \[REMOVED\] Battle Videos
* \[UPDATED\] Options Menu
  * Renamed "Party/Box" to "Send To Boxes"
    * Manual
    * Automatic
  * Give Nicknames \[ON/OFF\]
  * Gyroscope \[ON/OFF\]
  * Vertical Camera Controls
    * Regular
    * Inverted
  * Horizontal Camera Controls
    * Regular
    * Inverted
  * Autosave \[ON/OFF\]
  * Renamed "Button Mode" to "Casual Controls". You can play with one hand.
  * Show Nicknames \[ON/OFF\]
  * Skip Movies \[ON/OFF\]
    * \(This thing doesn't even work properly\)
  * Sound Options.
    * If you want an example of VERY WEIRD and POINTLESS game design. You need to talk to an NPC at the first gym city in order to get the "Hi-tech Earbuds" this key item will unlock the Sound Options. So, if you don't ever talk to this NPC in this game that doesnt incentive exploration, you can't change the sound options, it's missable.
    * Background Music \[0-10\]
    * Sound Effects \[0-10\]
    * Pokemon Cries \[0-10\]
* \[IMPORTANT\] Pokemon can evolve even if they are Level 100. You give them a rare-candy.
  * Great improvement.
* Post Game
  * Complete the 400 Pokemon Pokedex
  * Complete the siblings episode.
    * Capture your legendary mascot here? This

[Return to Navigation](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#quick-navigation)

## Appendix

## The Complexity of So Many things...

We now have a close approximation of how many Pokemon forms, abilities, items and moves are available in the game. The most time consuming forms are the battle forms, since they require more testing time, "skin" forms if well implemented should not mess with battle-tests. Game Freak is not giving support to 890 Pokemon, but in reality they are giving support to much more.

* Data-wise total Pokemon: 890+205=1095
  * Total Species: 890 \(8th Generation\)
  * Battle Impact
    * Battle Variations are considered for calculation.
    * Species: 136
    * Variations: 205
  * Non-Battle Impact
    * There are species with both battle and non battle variations.
    * Species: 119
    * Variations: 257
* Number of Moves: 804 Moves
* Number of Abilities: 258 Different Abilities
* Approximately ~ 950 different items from 8 generations, but not many return.

My software engineering career experience allows me to explain how support for these Pokemon, Moves, Abilities and Items should not something to be aware for the battle-system. Websites like amazon, youtube, netflix,etc are handling MILLIONS/BILLIONS of data structures per day with their systems running. Pokemon data is isolated in-game and it can run offline, "thousands" are nothing to what Software engineers should be worring about. Their mindset is to think is many many ways of how to solve the complexity of their systems. If there are issues with supporting all of this things, they need to rework their engineering, MMOs have more content \(numbers wise\), think of it World of Warcraft has 15 years giving support to their platform, they easily exceed the 900 items and they are running an always online game. Game Freak is not handling their methods and data-structures in efficient ways if they think think they can't support this the battle system, they just need more testing tools, automated tests for all the scenarios, that is worth for Research and Development.

## Forms Considerations

Many of these Pokemon have their small differences, making it a small segregation between species, here's the "total" of Pokemon in terms of data-structureness.

* I will add two classifications for forms. And the main rule to make a distinction is if the form has an impact in battle.
* Even if they look different in Boxes doesn't mean they have an impact in battle.
* Below these 2 classifications you can see the different segregations for Pokemon variants, such as "formes", gender, mega evolutions, gigantamax.
* I will subsctract 1 to the full variation list to take into the account only the variations, removing the original forms for the species.

### Variations that have an Impact in Battle: 205 Variations from 136 Species

They are not split with species, and the original form is ignored, we are counting non-original forms.

* Special Cases are for Pokemon multiple DIFFERENT forms. Eg. Having Megas and Gigas. Is different than having 3 forms like Deoxys.

```text
    - Total: 53+7+30+32+17+13+28+25=205 Forms from 41+7+26+11+13+8+7+23=136 Species
    - Kanto: 16+11+16+5+5= 53 Forms from 4+11+16+5+5= 41 Species
        - Special Cases: 8+3+3+2=16 Forms from 4 species
            - Pikachu (8)
                - 7 Cosplays
                - 1 Gigantamax
            - Charizard (3)
                - 2 Mega Evolutions
                - 1 Gigantamax
            - Meowth (3)
                - 1 Alolan Form
                - 1 Galar Form
                - 1 Gigantamax Form
            - Gengar (2)
                - 1 Mega Evolution
                - 1 Gigantamax
        - Mega Evolutions: 11 Forms from 11 Species
            - Venasaur (1)
            - Blastoise (1)
            - Beedrill (1)
            - Pidgeot (1)
            - Alakazam (1)
            - Slowbro (1)
            - Gengar (1)
            - Kangaskhan (1)
            - Pinsir (1)
            - Gyarados (1)
            - Aerodactyl (1)
        - Alolan Variants: 16 Forms from 16 Species
            - Ratatta (1)
            - Raticate (1)
            - Raichu (1)
            - Sandshrew (1)
            - Sandslash (1)
            - Vulpix (1)
            - Ninetales (1)
            - Dugtrio (1)
            - Persian (1)
            - Geodude (1)
            - Graveler (1)
            - Golem (1)
            - Grimer (1)
            - Muk (1)
            - Exeggutor (1)
            - Marowak (1)
        - Gigantamax 5 forms from 5 Species
            - Butterfree (1)
            - Machamp (1)
            - Kingler (1)
            - Lapras (1)
            - Eevee (1)
        - Galar Variants 5 forms from 5 species
            - Ponyta (1)
            - Rapidash (1)
            - Farfetch'd (1)
            - Weezing (1)
            - Mr. Mime (1)
    - Johto: 7 Forms from 7 Species
        - You can see how forgotten Johto pokemon are.
        - Mega Evolutions: 6 Forms from 6 Species
            - Ampharos (1)
            - Steelix (1)
            - Scizor (1)
            - Heracross (1)
            - Houndoom (1)
            - Tyranitar (1)
        - Galar Forms
            - Corsola (1)
    - Hoenn: 3+3+20+2+2=30 forms from 1+1+20+2+2=26 Species
        - Castform (3)
        - Deoxys (3)
        - Mega Evolutions: 20 Forms from 20 Species
            - Sceptile (1)
            - Blaziken (1)
            - Swampert (1)
            - Gardevoir (1)
            - Sableye (1)
            - Mawile (1)
            - Aggron (1)
            - Medicham (1)
            - Manetric (1)
            - Sharpedo (1)
            - Camerupt (1)
            - Altaria (1)
            - Banette (1)
            - Absol (1)
            - Glalie (1)
            - Salamance (1)
            - Metagross (1)
            - Latias (1)
            - Latios (1)
            - Rayquaza (1)
        - Primal Reversion: 2 Forms from 2 Species
            - Kyogre (1)
            - Groudon (1)
        - Galar Forms: 2 Forms from 2 Species
            - Zigzagoon (1)
            - Linoone (1)
    - Sinnoh: 2+1+5+1+1+17+5=32 Forms from 11 Species
        - Wormadam (2)
        - Cherrim (1)
            - Cherrim's Ability is what buffs it. Not his form. But since there's this coupling with the form and ability, it will be on the impact list.
        - Rotom (5)
        - Giratina (1)
        - Shaymin (1)
        - Arceus (17)
            - Normal type doesn't count
        - Mega Evolutions: 5 Forms from 5 Species
            - Lopunny (1)
            - Garchomp (1)
            - Lucario (1)
            - Abomasnow (1)
            - Gallade (1)
    - Unova: 11+4+2=17 Forms from 13 Species
        - Basculin (1)
        - Darmanitan (1)
        - Tornadus (1)
        - Thundurus (1)
        - Landorus (1)
        - Kyurem (2)
        - Keldeo (1)
        - Meloetta (1)
        - Genesect (4)
        - Mega Evolutions
            - Audino (1)
        - Gigantamax
            - Garbodor (1)
        - Galar Forms
            - Darumaka (1)
            - Darmanitan (1)
    - Kalos: 1+1+1+1+3+3+1+2=13 Forms from 8 Species
        - Why would Kalos not add Megas for Kalos Pokemon?
        - Mega Evolutions
            - Diancie (1)
        - Ash's Greninja (1)
        - Meowstic (1)
            - A gender difference. Special case because they have differences that affect battles.
        - Aegislash (1)
            - Like Cherrim, its ability has the impact, not really the form, but still coupled.
        - Pumpkaboo (3)
            - Stats change
        - Gourgeist (3)
            - Stats change
        - Hoopa (1)
        - Zygarde (2)
    - Alola: 3+2+1+17+1+1+3=28 Forms from 7 Species
        - Oricorio (3)
        - Lycanroc (2)
        - Wishiwashi (1)
        - Silvally (17)
            - Normal type doesn't count
        - Minior (1)
            - One Core form is considered here.
        - Mimikyu (1)
            - Ability makes it change form.
        - Necrozma (3)
    - Galar: 2+2+1+1+1+1+1+16=25 Forms from 23 Species
        - Cramorant (2)
            - Wasn't sure if I was gonna add it, but its like Cherrim and Aegislash.
        - Toxtricity (2)
            - Nature and different abilities add an impact, they also learn different moves.
            - Gigantamax
        - Alcremie (1)
            - Gigantamax.
        - Eiscue (1)
            - Stats change.
        - Indeedee (1)
            - A gender difference that change stats. Similar to Meowstic.
        - Morpeko (1)
            - One move changes type
        - Zacian (1)
        - Zamazenta (1)
        - Gigantamax: 16 Forms from 16 Species
            - Melmetal (1)
                - Considered in Galar as Let's go are not considered at all.
            - Corviknight (1)
            - Orbeetle (1)
            - Drednaw (1)
            - Toxtricity (1)
            - Coalossal (1)
            - Flapple (1)
            - Appletun (1)
            - Sandaconda (1)
            - Centiskorch (1)
            - Hatterene (1)
            - Grimmsnarl (1)
            - Alcremie (1)
            - Copperajah (1)
            - Duraludon (1)
            - Eternatus (1)
                - Unobtainable in game, only as boss fight.
```

### Variations/Skins that **DON'T** have an Impact in Battle: 257 Variations from 119 Species

Note: There are Pokemon that have forms with BOTH impact in battle and not impact.

```text
    - Total: 30+50+18+35+9+42+9+64=257 Variations 24+24+18+34+5+7+4+3=119 Species
    - Kanto: 23+7=30 Forms from 24 Species
        - Gender Based: 23 Forms from 23 Species
            - Venasaur (1)
            - Butterfree (1)
            - Rattata (1)
            - Raticate (1)
            - Pikachu (1)
            - Raichu (1)
            - Nidoran (1)
            - Zubat (1)
            - Golbat (1)
            - Gloom (1)
            - Vileplume (1)
            - Kadabra (1)
            - Alakazam (1)
            - Doduo (1)
            - Dodrio (1)
            - Hypno (1)
            - Rhynorn (1)
            - Rhydon (1)
            - Goldeen (1)
            - Seaking (1)
            - Scyther (1)
            - Magikarp (1)
            - Gyarados (1)
        - Ash Cap Pikachus (7)
    - Johto: 22+1+27=50 Forms from 22+1+1=24 Species
        - Gender Based: 22 Forms from 22 Species
            - Meganium (1)
            - Ledyba (1)
            - Ledian (1)
            - Xatu (1)
            - Sudowoodo (1)
            - Politoed (1)
            - Aipom (1)
            - Wooper (1)
            - Quagsire (1)
            - Murkrow (1)
            - Wobbuffet (1)
            - Girafarig (1)
            - Gligar (1)
            - Steelix (1)
            - Scizor (1)
            - Heracross (1)
            - Sneasel (1)
            - Ursaring (1)
            - Piloswine (1)
            - Octillery (1)
            - Houndoom (1)
            - Donphan (1)
        - Spiky-eared Pichu (1)
            - Locked in HeartGold and SoulSilver 🤷‍♂️
        - Unown (27)
            - Let's consider the P Unown the original form. P for Pokemon.
    - Hoenn: 18 Forms from 18 Species
        - Gender Based: 18 Forms from 18 Species
            - Torchic (1)
            - Combusken (1)
            - Blaziken (1)
            - Beautifly (1)
            - Dustox (1)
            - Ludicolo (1)
            - Nuzleaf (1)
            - Shiftry (1)
            - Meditite (1)
            - Medicham (1)
            - Roselia (1)
            - Gulpin (1)
            - Swalot (1)
            - Numel (1)
            - Camerupt (1)
            - Cacturne (1)
            - Milotic (1)
            - Relicanth (1)
    - Sinnoh: 31+2+1+1=35 Forms from 31+1+1+1=34 Species
        - Gender Based: 31 Forms from 31 Species
            - Starly (1)
            - Staravia (1)
            - Staraptor (1)
            - Bidoof (1)
            - Bibarel (1)
            - Kricketot (1)
            - Kricketune (1)
            - Shinx (1)
            - Luxio (1)
            - Luxray (1)
            - Combee
            - Roserade (1)
            - Pachirisu (1)
            - Buizel (1)
            - Floatzel (1)
            - Ambipom (1)
            - Gible (1)
            - Gabite (1)
            - Garchomp (1)
            - Hippopotas (1)
            - Hippowdown (1)
            - Croagunk (1)
            - Toxicroak (1)
            - Finneon (1)
            - Lumineon (1)
            - Snover (1)
            - Abomasnow (1)
            - Weavile (1)
            - Rhyperior (1)
            - Tangrowth (1)
            - Mamoswine (1)
        - Burmy (2)
        - Shellos (1)
        - Gastrodon (1)
    - Unova: 3+3+3=9 Forms from 3+1+1=5 Species
        - Gender Based: 3 Forms from 3 Species
            - Unfezant (1)
            - Frillish (1)
            - Jellicent (1)
        - Deerling (3)
            - Spring will be considered original.
        - Sawsbuck (3)
    - Kalos: 1+19+4+4+4+9+1=42 Forms from 7 Species
        - Gender Based
            - Pyroar (1)
        - Vivillon (19)
        - Flabebe (4)
        - Floette (4)
        - Florges (4)
        - Furfrou (9)
        - Xerneas (1)
    - Alola: 6+1+1+1=9 Forms from 4 Species
        - Minior (6)
            - Considering 6 different colors.
        - Solgaleo (1)
            - Radian Sun Phase (Not registered in Pokedex
        - Lunala (1)
            - Full Moon Phase (Not registered in Pokedex)
        - Marshadow (1)
            - Zenith ~ Not registered in Pokedex
    - Galar: 62+1+1=64 Forms from 3 Species
        - Alcremie (62)
            - Note: 7 Shiny forms, not 63, 1 per sweet.
        - Sinistea (1)
        - Polteageist (1)
```

### Classifications of Pokemon Forms

```text
- Total of Pokemon Forms including original forms: (321+99+50+30+27=527)
    - From 890 species, there are 527 different forms in 59+99+48+29+27=262 Species.
    - Shiny Total is pending as it not something you could do by just substracting totals.
        - You can think it's at least around ~1300 different Shinies, becausee Alcremie sabotages the Shiny Count.
    - Formes: 321 from 59 species.
    - Gender: 99 species
    - Mega Evolutions: (48+2=50 from 48 species)
        - Mega Evolutions: 48
            - 46 species mega-evolve.
        - Primal Reversion: 2 from 2 species
    - Regional Forms: 30 from 29 species (Meowth has 2 Regional forms)
    - Gigantamax: 27 from 27 species
        - Flapple and Appletun G-Max Move has a different impact in battle, so each counts even if its the same model.
```

#### Pokemon with "Formes"

* Includes original formes.
* Pokemon with Forms/Formes \(Total: 15+30+8+40+35+64+47+82=321 from 1+2+2+9+13+12+10+10= 59 species total\)
  * This is a complementary list to the previous lists of Pokemon forms with an impact in battle.
  * Many Pokémon have different forms. Either a re-color or a new design. 
  * Gender differences won't be listed here.
  * Regional forms won't be listed here, the community segregates them as regional, but they could fit here, if I were strict, but I'm sticking to the community.
  * Pokemon here will be listed in the generation they belong too, if forms were introduced in other generations this doesn't matter.
    * 1st Generation ~ Total: 15 from 1 species
      * Pikachu: \(15\)
        * 1 Original Pikachu
        * 7 with Cosplays
        * 7 more with Caps
    * 2nd Generation ~ Total: \(2+28=30 from 2 species\)
      * Pichu \(2\)
        * Original Pichu
        * Spiky-eared Pichu
      * Unown \(28\) 
        * Had 26 forms. 3rd generation added 2 new forms, for a total of 28.
        * According to Bulbapedia, punctuation Unown seem to have different stats for the Pokeathlon.
    * 3rd Generation ~ Total: \(4+4=8 from 2 species\)
      * Castform \(4\)
        * Depending on the weather this Pokémon will transform.
        * Not all weathers give him a form, Eg. Sandstorm.
        * Every form has different types.
      * Deoxys \(4\) 
        * Originally the form was linked to a specific game. If you had Pokémon FireRed, Deoxys would be the Attack Form.
        * From 4th generation and on, you could go to a meteorite and change its form.
    * 4th Generation ~ Total: \(3+3+2+2+2+6+2+2+18=40 from 9 species\)
      * Burmy \(3\)
        * This one changes if it participates in battle, but it doesn't have an impact.
        * Plant Cloak in grass areas.
        * Sandy Cloak in rocky areas. Caves and sand.
        * Trash Cloak in buildings/urban areas.
      * Wormadam \(3\)
        * This Pokemon can't change form, Wormadam depends on the form it had before evolving from Burmy. This is, if you had a Plant Cloak Burmy and it evolves it will transform into a Plant Cloak Wormadam.
        * Every form has different types.
      * Cherrim \(2\)
        * It changes during battle if there's Sunlight in the battlefield.
      * Shellos \(2\)
        * This is just for cosmetics. The fantasy tells us that at the Sinnoh Region this Pokemon was different on one side of Mt. Coronet and on the other side it would be different. Same stats, just different look.
      * Gastrodon \(2\)
        * Like Shellos, it's just a geo-fantasy form. As a personal side note, this could be the start of the "regional" forms. Depending on the location Pokemon would look different, this was the first case but on one specific region. Both Shellos and Gastrodon formes original fantasy is a somewhat abandoned in newer generations, depending of the game you have, its the one you can capture.
      * Rotom \(6\)
        * Like Deoxys' meteorites, you had to go to a specific place and change Rotom's form in that area by interacting with an object on map.
      * Giratina \(2\)
        * Narrative wise it's could also be considered a region/geographical form. If Giratina it's in the Pokemon world it would be the "Altered Form" Giratina, but when Giratina is in the Distortion World it will transform to its true self, the Origin Forme. You can force the Origin forme in the Pokemon World if you make Giratina hold the Griseous Orb. Exclusive to Platinum and onwards.
      * Shaymin. 2 Forms. Originally only one, but Platinum introduced the Sky Forme, you had to use a "Gracidea" Flower to activate its form.
      * Arceus ~ The God Pokemon  \(18\)
        * One for each pokemon type. Make Arceus hold a "Plate" and it will transform its type. This one is a simpler re-color from the original, not a complete redesign, so while they are "forms", we will call them "skins" in a graphic design point of view. \(Worth noting that a 19 skin existed with the `??? Type`. Just in game data, but never present in official ways.\)
    * 5th Generation ~ Total: \(2+2+4+4+2+2+2+3+2+2+2+2+5=35 from 13 species\)
      * Basculin \(2\)
        * Forms Non-interchangeable. 
        * Just different forms with different abilities. 
        * Same stats and types.
      * Darmanitan \(2\)
        * If Darmanitan has the "Zen Mode" Ability, it can transform _during battle_ to the Zen Mode Form. If Darmanitan has less than 50% of its health it changes. This Zen Mode is Fire/Psychic and its stats change.
      * Deerling \(4\)
        * Remember, The fifth generation has a unique mechanic: seasons. 
        * Deerling changes form depending of the season; Spring, Summer, Autumn, Winter.
      * Sawsbuck \(4\)
        * Identical to Deerling. The issue is that since this mechanic was deprecated/abandoned, you can only get Summer,Autumn and Winter forms if you transfer them from the Fifth generation.
      * Tornadus \(2\)
        * Use a _Reveal Glass_ to transform to its Therian Form. This form is exclusive to Pokemon Black and White 2 and onward.
        * Originally blocked behind a  $3 dollar cash-wall.
      * Thundurus \(2\)
        * Identical to Tornadus.
      * Landorus \(2\)
        * Identical to Tornadus.
      * Kyurem \(3\)
        * By using a DNA Splicer you can transform Kyurem to either a Black Kyurem or a White Kyurem. This will fuse a Reshiram or Zekrom from your game  and fuse it with Kyurem, if you use the Splicers again, it will return your Reshiram or Zekrom to you. When fused, you "lose" your one pokemon, but don't worry just unfuse them to recover it.
      * Keldeo \(2\)
        * If Keldeo knows the move _Secret Sword_ it can change to _Resolute form_, if it forgets the move, it will return to the original game. This form is exclusive to BW2.
      * Meloetta \(2\)
        * 2 Forms. Use _Relic Song_ in battle to change between the 2 forms.
        * Stats change
        * Types change
      * Reshiram \(2\)
        * Overdrive Mode. Not even considered in the Pokedex.
        * Just a battle animation.
      * Zekrom \(2\)
        * Overdrive Mode. Not even considered in the Pokedex.
        * Just a battle animation.       
      * Genesect \(5\)
        * Identical to Arceus, make it hold a _Drive_ and it will change the color of its back, which is where it loads the drive. The _drive_ changes the type of its signature move _Techno Blast_.
    * 6th Generation ~ Total: \(2+20+5+5+5+10+2+4+4+2+3+2=64 from 12 species\)
      * Greninja \(2\)
        * Okay, this other form is a very different one. While Greninja debuts in the 6th generation, it gets a new form in the 7th generation. The thing is that only if you get a Greninja with the _Battlebond_ ability, then you can have this special form. There are 2 things that I don't like about this form, it changes its stats by a lot, plus the _Water Shuriken_ move will always hit 3 times, but the worst thing about this \(personally\) is the combination of better stats plus the fact that its appearance resembles Ash, from the Anime. Anime and games are different stuff, the Ash resemblance makes me think this is Digimon. \(Note: I also like Digimon, but this is Pokemon, so, I don't like the Ash thing here\)
      * Vivillon \(20\)
        * 2 exclusive event patterns... for a total of 20.
        * Somewhat similar to Shellos. Narrative-wise, this could have been a Regional Form, since the Patterns are geographical based in our world, not the pokemon world. If this took place in the Pokemon world it could have a pattern per region and even universes.
        * Same stats
        * Very hard to get them all
      * Flabébé \(5\)
        * It depends on which Flower patch you find the Pokemon. Red, Yellow, Orange, Blue or White, like Arceus, and Genesect. It's just a recolor, not a redesign. You can't change the form.
      * Floette \(5\)
        * Evolve Flabébé.
      * Florges \(5\)
        * Evolve Floette.
      * Furfrou \(10\)
        * They are very different visually, and stats stay the same. But this was more work from the creative team, as this is not a recolor or a harder tweak like Vivillon.
      * Aegislash  \(2\) 
        * It's not 100% a form, it's called stance, but still counts as form for the document. The idea here would be to think how the Pokemon would look when attacking or defending. This is similar on when you create a character and you have to know how does it look when its happy, sad, angry, etc. Imagine if every Pokemon would change form if they were laying down, or running, stuff like that, funny, eh?
        * Stances changes its stats.
      * Pumpkaboo \(4\)
        * Different sizes, you just change model's size.
        * Stats change with each form.
      * Gourgeist \(4\)
        * Identical to Pumpkaboo
      * Xernas \(2\)
        * These are fantasy forms. 
        * When in battle Xernas has a "Active Mode".
        * When it's outside battle is in "Neutral Mode". 
      * Zygarde \(3\)
        * In 6th generation it only had one form. In 7th generation it got 2 more. The 6th generation form is the "50% Forme", it looks like a Snake. 
        * Fans often made theories that Zygarde's story content was cut from the sixth generation. Players had to wait until the 7th generation to know more about this Pokemon. It even became a sort of a gimmick in the game, where you had to collect the cells and cores of the Pokemon.
        * A Dog like form is called "10% Forme" it has different stats. 
        * A humanoid form is called the "Complete Forme". It has much much better stats. There were theories that this was a fusion with Xernas/Yveltal \(6th generation mascots\) considering it adds blue and red colors and not just green.
        * They gave somewhat importance to this Pokemon, but at the same time it's just a side-quest, it's just something to fill the content that would probably be better to be implemented in the 6th generation, even characters from the 6th generation are the ones that will tell you about the cells and cores of this pokemon.
        * You have to assemble/disassemble Zygardes if you want to get different forms. 
        * Core and cells are "other forms", but they won't be considered for the games.
      * Hoopa \(2\)
        * Using a Prison Bottle it will change its form, similar to Shaymin. 
        * Design changes, stats changes and even types changes.
    * 7th Generation ~ Total: \(4+3+2+18+8+2+2+2+4+2=47 from 10 species\)
      * Oricorio \(4\)
        * These are called styles, the fantasy is that depending on the dance style, the pokemon changes its appearance. 
        * Different designs and types. You can change the style by using a flower nectar. 
        * It's signature move type changes depending on the style.
      * Lycanroc \(3\)
        * When Rockruff evolves into Lycanroc depending on the version you have. 
        * Ability Changes.
        * Midday Form. Only in the Sun versions and during the day.
        * Midnight Form. Only in Moon versions and during the night.
        * Dusk Form. Between 5pm and 5:59 pm. Additionally it must have the Own Tempo ability.
          * Own tempo Rockruffs were only obtained via event. \(You can breed them, thought\)
          * It's only available in the Ultra Versions.
        * Different design, stats.
      * Wishiwashi \(2\)
        * While in-game they are technically 2 forms. In a narrative point of view, it's a bunch of Wishiwashis schooling, and remember, there's strength in Unity. 
        * To be able to use a "School Form", Wishiwashi must be at least level 20 and it will automatically change form at the beggining of the battle. 
        * It will return to be a single Wishiwashi when it has less than 25% health, this form is called "Solo Form".
      * Silvally \(18\) 
        * Extremely identical to Arceus, it was based in Arceus. Instead of using "plates" this Pokemon uses "memories". Like Arceus if you change the memory, it will change forms and this is only a re-color.
      * Minior \(8\)
        * 2 Forms but one of those forms has 7 different "skins". \(1+7\)
        * When Minior is above 50% health it will be in "Shell Form", it will change to "Core Form" below 50%. Core Forms skins can not be changed, the Minior you find will always have that skin. 
        * Every core skin is based in the Rainbow, that's why there are 7 colors.
        * Forms have different stats and designs, as mentioned before, skins are not a redesign, but a recolor.
      * Mimikyu \(2\)
        * When gets attacked changes "form", its disguise gets compromised.
      * Solgaleo \(2\)
        * Radian Sun Phase. Not even considered in the Pokedex.
        * Just a battle animation.
      * Lunala \(2\)
        * Full Moon Phase. Not even considered in the Pokedex.
        * Just a battle animation.
      * Necrozma \(4\)
        * Similar to Kyurem. 
        * There's a "normal" Necrozma. Like the DNA Splicers, this Pokemon will fuse with a Solgaleo or Lunala, you will lose your Solgaleo/Lunala but you can recover it if you unfuse them. Sadly, Necrozma needs 2 different items to fuse, instead of one \(like Kyurem\). 
        * Lunala fusion using the N-Lunarizer to get Dawn Wings Necrozma
        * Solgaleo fusion using the N-Solarizer to get Dusk Mane Necrozma
        * The third form is called "Ultra Necrozma", but the gimmick here its that it needs to be transformed in either "Dusk Mane" or "Dusk Wings". Make it hold the "Ultranecrozium Z" and then use the move "Ultra Burst" in the Battle screen and it will transform. It works like a Mega Evolution or Primal Reversion.
      * Marshadow \(2\)
        * Zenith not even considered in the Pokedex.
        * Just a battle animation.
    * 8th Generation ~ Total: \(3+2+63+2+2+2+2+2+2+2=82 from 10 species\)
      * Cramorant \(3\)
        * It has small similarities with Wishiwashi's since depending of health it will change. But this forms actually goes into the same category as Aegislash. Ir's also a bit hard to add, but I won't add it.
        * Gulping Form
        * Gorging Form \(this one is so funny\)
      * Toxtricity \(2\)
        * Different moves
        * Nature is coupled with forms.
      * Alcremie  \(63\)
        * The Pokemon with most forms as of 8th generation, they are all skins.
        * Having this many skins sabotages the count of all forms in all generations for comparison, it's an atypical value for measurement.
      * Sinistea \(2\)
        * Just a small and great detail regarding porcelain. Fits more into a skin, a very rare skin.
        * Forgery Form
        * Authentic Form
      * Polteageist \(2\)
        * Same as preevolution.
      * Eiscue \(2\)
        * Very similar to Mimikyu's.
        * It's stats change when changes form.
      * Morpeko. \(2\)
        * More than a form, this is calleed "Mode". But it's pretty much the same. The only difference is the fact that if Morpeko uses the move "Aura Wheel" it will have a different type, alternating between Electric or Dark type. 
        * Same form category as Aegislash.
      * Zacian \(2\)
        * Hero of Many Battles Form
        * Crowned Sword
          * If you make it hold the Rusted Sword
          * Types change
          * Stats change
      * Zamazenta \(2\)
        * Hero of Many Battles
        * Crowned Sword \(I guess this is Crowned Shield?\)
          * If you make it hold the Rusted Shield.
          * Types change
          * Stats change
      * Eternatus \(2\)
        * Eternamax Eternatus can't be obtainable for players, at game's launch it serves as a boss.

#### Gender difference Forms

* Gender Forms \(22+22+18+31+3+2+0+1= 99 Pokemon with gender differences\)
  * Kanto: 22 Pokemon have new gender differences
    * Remember that Nidoran 🚹 and Nidoran 🚺 were the first pokemon with a notorius difference?
    * Let's Go Eevee has a gender differences, but it won't be taken in consideration
      * Venasaur
      * Butterfree
      * Rattata
      * Raticate
      * Pikachu
      * Raichu
      * Nidoran
      * Zubat
      * Golbat
      * Gloom
      * Vileplume
      * Kadabra
      * Alakazam
      * Doduo
      * Dodrio
      * Hypno
      * Rhynorn
      * Rhydon
      * Goldeen
      * Seaking
      * Scyther
      * Magikarp
      * Gyarados
  * Johto: 22 Pokemon have new gender differences
    * Meganium
    * Ledyba
    * Ledian
    * Xatu
    * Sudowoodo
    * Politoed
    * Aipom
    * Wooper
    * Quagsire
    * Murkrow
    * Wobbuffet
    * Girafarig
    * Gligar
    * Steelix
    * Scizor
    * Heracross
    * Sneasel
    * Ursaring
    * Piloswine
    * Octillery
    * Houndoom
    * Donphan
  * Hoenn: 18 Pokemon have new gender differences
    * Torchic
    * Combusken
    * Blaziken
    * Beautifly
    * Dustox
    * Ludicolo
    * Nuzleaf
    * Shiftry
    * Meditite
    * Medicham
    * Roselia
    * Gulpin
    * Swalot
    * Numel
    * Camerupt
    * Cacturne
    * Milotic
    * Relicanth
  * Sinnoh: 31 Pokemon have new gender differences.
    * Starly
    * Staravia
    * Staraptor
    * Bidoof
    * Bibarel
    * Kricketot
    * Kricketune
    * Shinx
    * Luxio
    * Luxray
    * Roserade
    * Combee
    * Pachirisu
    * Buizel
    * Floatzel
    * Ambipom
    * Gible
    * Gabite
    * Garchomp
    * Hippopotas
    * Hippowdown
    * Croagunk
    * Toxicroak
    * Finneon
    * Lumineon
    * Snover
    * Abomasnow
    * Weavile
    * Rhyperior
    * Tangrowth
    * Mamoswine
  * Unova: 3 \(Very notorious differences, like the Nidorans\)
    * Unfezant
    * Frillish
    * Jellicent
  * Kalos: 2 \(Very notorious differences\)
    * Pyroar
    * Meowstic
      * Different moves and abilities
  * Alola: 0
  * Galar: 1
    * Indeedee
      * Different stats

#### Regional Forms

* Regional Forms \(17+13 = Total 30\)
  * Alolan Forms \(17\)
    * Ratatta
    * Raticate
    * Raichu
    * Sandshrew
    * Sandslash
    * Vulpix
    * Ninetales
    * Dugtrio
    * Meowth
    * Persian
    * Geodude
    * Graveler
    * Golem
    * Grimer
    * Muk
    * Exeggutor
    * Marowak
  * Galar Forms \(13\)
    * Meowth
    * Ponyta
    * Rapidash
    * Farfetch'd
    * Weezing
    * Mr. Mime
    * Corsola
    * Zigzagoon
    * Linoone
    * Darumaka
    * Darmanitan
    * Yamask
    * Stunfisk

#### Mega Evolutions

* Mega Evolutions and Primal Reversion \(Total: 50\)
  * \(Identation means they were introduced in OR/AS\)
  * Venasaur
  * Charizard X
  * Charizard Y
  * Blastoise
    * Beedrill
    * Pidgeot
  * Alakazam
    * Slowbro
  * Gengar
  * Kangaskhan
  * Pinsir
  * Gyarados
  * Aerodactyl
  * Mewtwo X
  * Mewtwo Y
  * Ampharos
    * Steelix
  * Scizor
  * Heracross
  * Houndoom
  * Tyranitar
    * Sceptile
  * Blaziken
    * Swampert
  * Gardevoir
    * Sableye
  * Mawile
  * Aggron
  * Medicham
  * Manetric
    * Sharpedo
    * Camerupt
    * Altaria
  * Banette
  * Absol
    * Glalie
    * Salamance
    * Metagross
    * Latias
    * Latios
    * Rayquaza
    * Lopunny
  * Garchomp
  * Lucario
  * Abomasnow
    * Gallade
    * Audino
    * Diancie

      **Primal Reversion**
* Groudon
* Kyogre

#### Gigantamax Forms

* Gigantamax ~ Total: 27 from 27 species
  * Pokemon with Gigantamax available at launch.
  * Flappel and Appletun have the same form, but since they have a different move, it will count twice, as it has a battle impact.
    * Charizard
    * Butterfree
    * Machamp
    * Gengar
    * Kingler
    * Lapras
    * Garbodor
    * Corviknight
    * Orbeetle
    * Drednaw
    * Coalossal
    * Flapple
    * Appletun
    * Sandaconda
    * Centiskorch
    * Hatterene
    * Grimmsnarl
    * Alcremie
    * Copperajah
    * Duraludon
  * Gigantamax Special Cases
    * Pikachu
      * Can only obtain it if you have a save file of Pokemon Let's Go Pikachu on your Nintendo Switch. For the average consumer, this is a $60 dollar Pokemon. Yes, you can ask someone to burrow their games, and players will just create a save file to unlock this Pokemon, it's not practical.
    * Meowth
      * Limited time event in Mistery Gift. Expected to end distribution in early 2020.
    * Eevee
      * Same as Pikachu, but with Let's Go Eevee
    * Snorlax
      * Not available at launch, but became available with an Online Update, making it available to appear and catch at dens, during the time of this writing this document it is unknown if it will stop appearing after January.
    * Melmetal
      * Unobtainable at launch by no legal means at the time of writing this document. \(Game manipulation doesn't count\)
    * Toxtricity
      * Unobtainable at launch by no legal means at the time of writing this document.
    * Eternatus
      * While it has a Gigantamax form, once you capture this Pokemon, you can't access to its Gigantamax form, this is the first time we see this kind of "Pokemon Boss" do that.

## Attack Dex

Here's my account with across the different generations. Total: 165+86+103+113+92+62+103+80= 804 Moves up to 8th generation.

* Attack dex Gen 1: 165
* Attack dex Gen 2: Added 86 Moves
* Attack dex Gen 3: Added 103 Moves
* Attack dex Gen 4: Added 113 Moves
* Attack dex Gen 5: Added 92 Moves
* Attack dex Gen 6: Added 62 Moves
* Attack dex Gen 7: Added 103 Moves
  * 18 Type Z-Moves
  * 17 Unique Z-Moves
  * Let's go games added 14 moves that were added to Galar later.
* Attack dex Gen 8: Added 80 Moves
  * Gen 8 Normal moves: 35
  * Dynamax Moves: 19 Moves
    * 1 for each type
    * 1 extra for normal. Max-Guard
  * Gigantamax Moves: 26 Moves
  * Removed 144 moves. This never happened before in past generations.

According to the attack dex: 724 moves Accorrding to Bulbapedia 822 different moves in Gen 8. There's some discrepancy. But I believe my personal count was makes the job done.

## Ability Dex

[Here's the complete list](https://bulbapedia.bulbagarden.net/wiki/Ability#List_of_Abilities), but I will be adding how many were added in each game. Remember that Abilities were introduced in the third generation, and abilities are game mechanics, they can mess with the game-state.

Another good thing to take into account is the fact that MANY abilities have an Overworld effect, not just a battle effect. For example, one of the most common used is Magma Armor, which makes Pokemon eggs hatch faster.

* Total: 76+47+41+27+42+25=258 Abilities up to  8th generation.
* Third Generation: 76 \(77, but one of them was never used\)
* Fourth Generation: 47
* Fifth Generation: 41
* Sixth Generation: 27
* Seventh Generation: 42
* Eight Generation: 25

## Items Info

Up until Gen 7, there's 959 different items, although there are many blanks in the item indexes, some items are just "???", literally. So it's around 900 items\(considering all item types, even Key Items\).

[Return to Navigation](software-engineering-exercise-patch-notes-on-every-pokemon-generation.md#quick-navigation)

