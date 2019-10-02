---
description: >-
  This is a very long essay, as it analyzes pretty much all the Legend of Zelda
  game in a technical way, this post is aimed for enthusiasts of how things work
  from the inside.
---

# Components of a Top Down Game 🎮 ~ A Legend of Zelda Case Study

I've been thinking for a long time that I should create a database of in-game components, or a list of things that have to be created to put in-game. While is intented to help me visualize what is needed in a video game, it should also be helpful for others. I'm going to use the very First Legend of Zelda for this, and then \(if no other project intervenes\) use a second top down game, to see how many similiraties exist. The reason why Mario Maker exists and why you can skin the game with the different Mario styles, it's because there are design patterns in those games, and naturally, top down games have the same too. Who knows, this could potentially be a Youtube video for later. 🎥

### Screens

#### Title Screen

The first thing you will notice is a title screen in games \(ignoring that at some point, splash screens are the first things we see\). The objective of this screen is to present the game without playing. Old video games used to present an intro to the game or show how the games were played. This screen is the lobby before an adventure. In The Legend of Zelda

![](https://i.ytimg.com/vi/yjmeb7HCeyU/hqdefault.jpg)

* You can see it presents an animated logo of the game.
* The year it was created
* The studio/company who created this game
* An background
* An animated waterfall \(which appends to the background\)
* The "Press Start Button" text that indicates, well, that same thing, that you should press the start button to trigger another action. \(Which takes you to the next screen\)

As mentioned before, the title screen presents the game, but you are not playing just yet. A programmer must

* Place the background image on the screen.
* Play the title screen music
* Animate any sprites that need to be animated.
  * The waterfall
  * The logo
* Animate and make that "darkening" of the sprites before the transition to the next screen.
  * Once the darkening has been completed the transition begins.

    ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/66a009cd6e65e43351e12c830a944dd2/image.png)
* Detect input for "Push Start Button"
  * This will trigger a transition to the file select screen
* Create transitions
  * To the Intro Screen
  * To the File Select screen
* There's an invisible logic here. Which is probably a timer. After a certain amount of time, if the player doesn't push the start button.
  * The Screen must go dark
  * Must make a transition to the `Intro Screen`

#### The Intro Screen

We could say that this is a separated screen even if they share the same song. This is a scrolling screen where that presents

* A big text with the story of the game. Also take into account that someone has to create the frame of the intro, which is the same frame around the game's logo.

  ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/038f07e425ccb9ff2310c2b694aa57e1/image.png)

* The list of treasures in 2 columns.

  ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/36545eaf5462d2f9bfff8b1f684e5522/image.png)

Next, you will notice that after a bit of spacing, the "all treasures" section appears.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/b54277e12dabb33a84b0ee722e9bdfad/image.png)

You can notice that same sprites for the frame are used as a separator for the section, as well as the sprite letters. I think it's easier to do the separator with the game engine, since you can make a grouped object containing the frame and the letters.

Next, you will notice that for the `34 treasures` here \(plus one, which is the triforce\), we can create a common object with the Treaure sprite and the label of the treasure. We would have a base item like this, the idea is to use this same item 35 times, 17 times on the left column, 17 times on the right column and make a specialized animated version, for the `Heart`, `Rupee` and `Triforce`.

This is the base item that we will need. As I mentioned before, this is represented by the treasure sprite and the label with the treasure's name.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/f827d28ed76c18ac1127a845f49673d6/image.png)

The next thing to do, would be either manually or by code, to place the the treasures on a column invisible object and just scroll the items.

* At the very end, the game suggests the player to take a look at the game manual.

Yet these two sprites are going to stay centered on the screen and they still stop at the very center. These two can be a third invisible center column with their own logic.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/aaef573293d5b2d506e13b03b74c3724/image.png)

So, in these screen the sprites for every treasure are used. They must be ready here, but a placeholder can be used. **There's a total of 35 treasures in this screen.**. Notice that the triforce is animated too.

A final transition will be made, it can be once the song has finished playing, we are going to transition to the `Title Screen`.

#### The File Select Screen

This screen is the hub to select your file. A file saves data for your personal adventure. This screen was made so you can have up to three different adventures, or that three different players could play the game in different times by sharing the cartridge. ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/8906a3029a72c3589c0949f9ed873953/image.png)

This screen has a solid black color background. There are labels to indicate information on the screen. If you press the "Select" button you can change between files and the last two options, which are "Register your name" and "Elimination mode".

* The heart to the left is the cursor of the current selection.
  * By pressing Select you move to the next selection.
* There are three file rows.
* There's a Link "Icon"/"Sprite" to represent the game character.
  * First Column
    * There's a name to that character
    * There's a death count. This is, how many times you have died during your adventure.
  * Second Column
    * A row of heart sprites to indicate how much health the player has collected during the adventure. The player starts with three hearts.

      **The Register your Name Screen**

      ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/88cf1e25f4f6535f53cedfda84b0826d/image.png)

This screen will prompt the player to name the main character/protagonist. While the canonical name is `Link`, the player can choose to name it whatever they want.

Here the player will only be able to select an "Empty" file, which is pretty much a file that doesn't have a name. It is worth noting that the player can name the three files in the same screen if they don't have a name. Once the "Register End" is selected, any files with 1 or more characters will be considered as playable files.

Once again, we can see here that _we are recyling Link's sprites_, the heart and there's a red square on the file selected. This red square represents the next letter that will be drawn, this is feedback for the player, this way will know how the position of the next letter.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/d1476c5b652b92fdd6881c4ac5ad21df/image.png)

At the bottom of the screen you can see a box with letters. Let's call it a Symbol Matrix. This 11x4 Matrix is where the player will choose the symbols for the name of main character. The gamepad's directional pad will move between the letters. Here, at the matrix, the purple frame is a resource that needs to be placed as well. If you press the A button, the selected letter will be added to the file name.

#### The Elimination File Screen

This is called "Elimination Mode". You will be transitioned here if you select the "Elimination Mode" from the "File Select Screen". ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/930af2f9efc58be5c927cae863fa6dac/image.png)

Similar to the other screens. You move between files using the "Select Button".

* Link sprite is here as well
* The heart sprite is now white.
* The Symbol Matrix doesn't do anything here. I would get rid of it.
* By Pressing the start button it will delete \(without any prompt\) the selected file. Design wise, it seriously needs to ask the player if its okay to delete everything from their adventure.
  * This will also play the Link's hurt sound effect
* Selectint "Elimination End" will make a transition to the "Register your name" screen

#### Gameplay Screen

Now that that player has selected the file they are going to play and pressed the "Start Button". There's going to be a transition that look like this. ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/ed4118850c02eace1b717759ce6aceba/tiWGnokSg2.gif)

**HUD**

The HUD \(Heads Up Display\) presents relevant information about the game. The NES Zelda HUD presents the following

* A `Minimap` of Hyrule
* How many rupees the player has
  * A HUD Rupee Icon is needed
* How many keys the player has
  * A HUD Key Icon is needed
* How many bombs the player has
  * A Bomb Key Icon is needed
* Which Item \(treasure\) is assigned to use with the B Button
* Which Item \(treasure\) is assigned to use with the A
  * As note, it's always a Sword
    * Wooden Sword
    * White Sword
    * Magical Sword
* The maximum Life the player has
* The current Life the player has

The HUD is always present during gameplay. This is the kind of information that the player must know all the time.

Observation: Notice how the purple frame from the Items is the same frame for the `File Select Screen`, `The Symbol Matrix` and the label separator `Register your Name` and `Elimination Mode`

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/8746caf12cb609a717d2ae2168442d66/image.png) ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/9e82532acabd999cd8acc07fa2a83691/image.png)

**Map**

The complete map is a:

* 4096 x 1344 pixels, 16 x 8 rooms, and 256 x 88 tiles in size
  * This is 128 rooms in total
* Tiles are 16x16 pixels^2
* Each "room" is 16x11 tiles

  **Minimap**

  ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/1a0f10c5d2f12a4df6963c48b7fad59b/image.png)

From the information about the map, the Minimap reflects this 16x8 matrix.

* The green dot on the grey rectangle represents the location of Link in Hyrule.
* If Link moves to another room, it must change to the new location.

#### The Rooms

Now that we talked more in depth about the HUD, we can talk about the rooms \(or areas\) of hyrule. Each room is 16x11 tiles. You might be asking what a Tile is... A tile is a sprite that is placed on a grid \(matrix\).

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/5d36889f700c762ff73bf7d8d19c7567/image.png) As you can see, there are many parts of this area that are pretty much the same thing. The main purpose of this was because of the limitations of the hardware of that time period, yet it's not a bad technique to create a map in any game, even today Observation: You can see that the cream color could just be the background and not a tile itself, the other tiles make the ilusion that the solid background could be another tile in Zelda for NES.

And many of these tiles are just a recoloration of other tiles to let the player think that it's a totally different area, take a look at this.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/d05763cd3e8ac367d6317fd1d880144e/image.png)

Those trees are the same thing, but different color, we call that a `re-color`!

#### Link

Now it's time to talk about the most complex system in this game, which is Link. Let's talk about the first thing that Link can do, moving.

**Link's Movement**

Link can move in the four cardinal directions \(North, West, South, East\), but we usually call them just `Up,Left,Down,Right`. And it has the following sprites.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/e625ef0f9b4dd40a602e2f4a8d9c8087/image.png)

In the previous image you can see 5 different sprites. These 5 sprites make the illusion of moving.

* First row are the `Down` Sprites
* Second row is the `Up` sprite. This sprite gets mirrored horizontally, and it makes the illusion of walk.
* Third row are the `Right` sprites, but just like the `Up`, if you mirror them, it will create the `Left` movement as well, there's no need for further movement.

#### Link taking damage

Link without Items is pretty simple. The other thing that Link can do without any items is.... to take damage. There's no different sprite, in this case Link's sprite flashes of different colors informing the player that Link has taken damage.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/e20ded1ae71bba4b5818f473400f87d0/VSGS5bZNPs.gif)

Link is pushed to the opposite direction where he's facing. Yet, it is not always the case, probably another way to push him would be to push him in the direction where the enemy that collides with Link is facing.

#### Link is defeated

When Link runs out of Life, he's defeated, it means there's a `Game Over`. ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/c4ff22276dcabfb27af363d8acef45fe/VP2oiN5MnV.gif)

* The Screen turns red
* A sound effect is played
* Link faces down and then the sprites rotates in all four directions.
* Link's faces Down
* The Screen darkens
* Link's sprite changes to grey
* A death animation is played. \(Like a small explosion\)
* Another sound effect is played
* The Game Over Screen label is shown at the center of the screen.

#### The Game Over Screen

#### Move between scenes

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/4e8d17aa80e698cd76eef8f90ef7beb4/n6sW6T8wpq.gif)

If you hold the Gamepad at the edge of the screen \(in this case holding the RIGHT button\) you can go to another room, this is how you travel around Hyrule. Here, there's a need for a camera, this camera will move to the next room and it will be rendered, this is a very simple camera, as it just moves to the center of the next screen.

* Notice how Link's move animation is played to the direction where he's moving.
* Enemies appear after the camera scrolls.

#### Collision detection

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/5d36889f700c762ff73bf7d8d19c7567/image.png)

Ok, so we do have our sprites on screen, but there has to be a disctintion between a sprite that can just walk over. Notice how Link can't get throught this sprites.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/665a89568b242744d719ee3eb16717d9/q1W7hahJkX.gif)

This has to be done, it's called Collision detection, and once detected, we are telling Link's sprite to not go throught them.

#### Link Gets an Item

The next sprite that needs to be created is when Link gets an Item. It looks like this. ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/3d3a5b3d47dfcab76813882649d1f399/image.png) This occurs after you get the Wooden sword.

#### Link using a Treasure

When Link uses a treasure \(or Item\), it will be using 1 of 3 new sprites. ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/bebe6ca25c210423f3dafa0716911fb0/Link_sword_attack.gif)

This is the most common thing you'll see, since you use the Sword all the time. Yet, when Link uses any treasure it uses the same sprites, only that they are sped up.

Here are the differences with some treasures.

E.g. The following is using bombs

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/a97adde278e69f9d819f9dbc6cead10b/LhlBNSfYkM.gif)

E.g. The following is using the Boomerang

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/3968d40216b14a712239cee8589cf9df/qx3DP8aPF3.gif)

This is different that the actual functionality of the Item. This section was about what Link does when using a treasure, which is pretty much `On Input`.

### Treasures

#### Active Treasures

Now it's the time to talk and analyze the treasures.

**The Shield**

Link's shield can block basic projectiles, such as arrows, the octorok rocks, yet it's not possible to block magical attacks. From what I can gather, there could be a child object in Link that has another collider, that would be the shield, the thing here would be to manipulate the collision box every time Link faces another place. When a basic projectile hits the shield:

* It will play a SFX
* It will destroy the projectile

There's an upgrade to the shield, the magic shield.

* It has a different sprite
* It has a bigger collision box \(so, it should be easier to block things\)

**Boomerang**

* It plays a continuous sound while traveling
* The sprite rotates indefintely until caught
* Travels to the direction where Link is facing
  * Althought it's not 100% true, it actually uses the current Input from the gamepad, you can throw a boomerang Diagonally.
* It will travel half the screen, starting from Link's hand position.
* When collides with most of enemies, it will stun them.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/3968d40216b14a712239cee8589cf9df/qx3DP8aPF3.gif)

Note: When upgraded to the Magical Boomerang, the only difference is that it can travel across the whole screen.

**Bomb**

* It plays a sound effect on spawn
* After about \[0.75 - 1\] seconds it will spawn an explosion that can damage enemies, this is a big collision box.
* It has an explosion animation using a single cloud sprite, the animation has 7 clouds. In this part of the animation where the enemies can get hurt.
  * There's another cloud effect that indicates that the explosion is fading.
  * From my understanding, enemies are not hurt from here, this is just a follow up.
* Bombs can open secret doors, on collision with an explosion the lock wil dissapear.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/a97adde278e69f9d819f9dbc6cead10b/LhlBNSfYkM.gif)

**Bow & Arrow**

In this game, these are considered two different items. Even if you manage to get arrows, you cant shoot'em, because you don't have a bow. On the other side, if you get the Bow but you don't have arrows, well, you can't shoot what you don't have. How does it work?

* The bow is just a requirement to shoot arrows \(you don't see Link using the arrow, just shoot an arrow in front of him.\)
* Spawn an arrow in front of where Link is facing.
* There's a sound effect when shoot
* The arrows follows the trajectory where Link is facing.
* It is destroyed
  * When it gets at the end of the screen
  * When it collides with an enemy
* You can see a destroyed animation

  ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/5f56a35b5c947ed8447355dba97a7656/9WMZ37bqWD.gif)

**Candle**

* It spawns a flame in front of Link
* A flame SFX plays
* The flame has an animation that makes you think the flames are moving
* The flame object moves aproximately 2 Units ahead of Link in a slow speed.
* The flame can hurt enemies
* The flame can hurt Link
* It dissapears after a couple of seconds

In dark rooms, the flame lights the way ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/32e79bf016e9b8a9b168efb28b73286f/O5D5kk9mdU.gif)

**Recorder**

This is a teleporter item. It takes you to other dungeons you have completed.

* It plays a Sound effect
* Every other game object in the game is frozen while the SFX plays.
* If you get hit, the tornado won't pick up Link
* It spawns a cloud on the 0,Y coordinate Link currently is.
* A tornado spawns from 0,Y of the screen
* The tornado moves horizontally across the screen
* The tornado has a "moving animation"
* IF it touches Link, Link's sprite disappears, making the player think its inside the tornado
  * Once it reaches the end of the screen, the game will make a transition \(apparently\) to a random room that has an entrance of a dungeon
  * Once at the new room, the tornado will repeat the spawn steps and move horizontally
  * Once it reaches the Center X, it will make the Link sprite appear.
  * The tornado will dissapear
  * Link will face to the right

    ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/485cd15082c0558c33b168e9cbcfe5ac/65M6vuO4BR.gif)

**Food**

This treasure's functionality is to make enemies think the food is Link, this is, bait. This is, enemies will now \(not always\) target the bait, instead of link. Note: Works as a usable key item to get past an enemy inside a dungeon. ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/87810d34e6c6e2f3c58905083a9edea7/ql1qLlbNdw.gif)

**Letter**

A treasure that by its own doesnt do anything. Nowadays it could be considered a Key Item, it is needed to "unlock" the potions by taking the letter to the old lady.

**Potions**

When you use a potion, every game object freezes and it waits until Link's health is completely refreshed. Once the red potion is used, there's a second potion that can be used as well. ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/14574f8c3b24ceb7a35affb9bf69f401/W1xnX3BcEI.gif)

**Magical Rod**

Pretty much the functionality of the sword, but this always shoots a projectile. What's important about this is how the sword code can be manipulated and recycled, changing stuff for the road.

Note: In order to be able to shoot a flame, the player must find a passive treasure called the "Book of Magic". The fire has the same functionality as the candle's fire, so, we would pretty much just instantiate a flame. ![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/ff5baad31574e6bc546f1c36cb9a54c1/Cn2uZ2bIvL.gif)

#### Passive Treasures

All of these treasures are not activable with B, rather, their effects are used in different conditions. As mentioned before, we would call this items nowadays as "Key Items"

**Raft**

The raft is a key item by itself, you can use it to cross the sea and reach a dungeon and an optional cave. This is what it does.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/def742f686220ca7acbec9fbfb93d166/7YJdRr4v2t.gif)

* Keep moving through the green wood
* The raft sprite will appear above Link
* Link's walking animation is activated
* The change screen logic is applied too, we will move to the next screen with it reaches the end of the screen.

**Book of Magic**

As mentioned before for the Magical Rod, if the player has collected this, it will allow the rod to spawn a flame on collision with an enemy or touching the edge of screen.

**Blue Ring**

This item pretty much just has to alter the logic of taking damage, in that function it will divide the damage by half.

* When collected it will change Link's sprite to a blue tunic.

**Red Ring**

Just like the blue ring, but this divides the damage by 4. Link takes a quarter of the original damage.

* When collected it will change Link's sprite to a red tunic.

These share pretty much all the functionality, just a matter of changing a 2 \(half damamge\) to a 4 \(quarter\) and changing the sprite to another one.

**Stepladder**

The stepladder is a very interesting item. The logic can be created in many many ways. And depending on how the map logic is created this item could be potentially be activated. Let's discuss the functionality first.

* The ladder lets you walk through an unwalkable tile \(that is not a wall\) where Link will place the ladder in front of him, this will allow Link to walk through

Here comes the interesting part, there are many unwalkable tiles in many rooms, yet apparently you can only use the stepladder where it could potentially be useful, notice how the two rooms are very similar, but you can only use the stepladder in one of them.

* It could be unlocked via a list of specific rooms where you could use it. \(It requires to makes this list, manually\)
* It could be unlocked by checking if there's a particular type of tile on that room, if that tile exists in that room, then you can use the stepladder \(this just requires to check the existence of it as a validation\)

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/1625f712721cdb0cf63aba2a8b2c6184/rBXgbOiTmj.gif)

**Keys**

The keys are items that allow you to unlock a door, that will the next room available to enter. As mentioned before the game keeps track of how many keys the player has.

* The player has to walk towards a locked door.
* If the player has at least one key, it will substract a key from the counter.
  * It will open the locked door, making the door object dissapear.

There's another item that the player can collect, it's called the magical key, this key allows the player to open any lock, removing the requirement of having keys.

**Power Bracelet**

When Link gets the power bracelet, it allows him to push these kind ofs rocks. It requires just a collision, and it requires that the tile in front of the rock is free of collisions.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/d6fe11cb17d7627ceb7dc55c9a47f95d/IJ1ib0TIOr.gif)

**Dungeon Map**

When you collect a Map in a Dungeon, the minimap will automatically fill the squares of the map, this way the player can see find the way around easily.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/fc626173ab32b51fd2dd5e4a73efad2f/image.png)

When you press start, you can see how the map is completed when you walk through rooms, sadly, collecting the `Dungeon Map` doesn't complete this map, yet it's useful to compare to where you have been. It even tells you which the directions where you can go, it's a nice bonus. \(Once again, the green square is Link. \)

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/73df1bb9f67797255d42677845ce2139/upload_5/14/2019_at_4_24_50_PM.png)

**Compass**

This is an item that every dungeon has, just like the Dungeon Map. Once you collect it, it will marked on the Minimap the of the Triforce Shard, this way the player will know where the Boss is located, so they can defeat it and get the Triforce Shard. It is not neccesary to get this shard in order to complete the dungeon.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/0ef5bf7b0adc76ef4927f0a405fe586d/fA0usOkIH8.gif)

**Triforce Shard**

Collecting a Triforce Shard doesn't do anything by themselves, they are just `Key Item`, they are only needed so the player can get throught a room at Level 9 ~ Death Mountain. If the player has completed the Triforce, then the player can proceed and have their adventure at the final dungeon, other than that they are useless.

* This item only has quick change color animation, the same sprite can be used and just change it's color back and forth.

#### Pick up treasures

These treasures have some similarities, like the way they spawn, and that they disappear if the player doesn't collect them. Also, some of them have an Idle Animation which is just changing colors. By the way, Link can collect these Items with his Sword, it becomes an extension of his collision box.

From the Wikia there's information about that, when Link defeats 10 enemies they will drop 5 Rupees. If the 10th enemy is defeated using a bomb, that enemy will drop 4 bombs. If Link defeats 16 enemies, they will drop a Fairy.

**Recovery Heart**

* When collected it will restore 1 Heart to the player's life. 
* You can collect as many as you want.
* If you have full life, nothing will happen, you will remain full health.
* When it spawns, it flashes quickly for a very very short time, it then changes to the Idle Animation.
* Has an animation, it changes to another color and goes back to the original one, this animation repeats indefinitely, for a total of 2 animations.
* If it's not collected until X amount of time, it will disappear.
* Enemies can drop this item when defeated.

**Heart Container**

* This item increases the player's max life. The player starts with 3 Hearts.

**Fairy**

Collecting a fairy restores Link's health by 3, it's pretty much 3 recovery hearts.

**Clock**

* When collected the enemies will freeze on their current position.
* When it spawns, it flashes quickly for a very very short time, it then changes to the normal sprite.
* If it's not collected until X amount of time, it will disappear.
* When it spawns, it flashes quickly for a very very short time, it then changes to an unanimated sprite.
* Enemies are STILL ANIMATED.
* Makes Link's sprite flash, this is the provided feedback to let the player know that the clock is under effect. The effect lasts until the player leaves the room.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/99044faeb7f02cc95d0e124f767bb089/5ZXPoIECJ4.gif)

As you can see the Clock doesn't have an Idle animation, it's just the sprite on screen.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/60426fd0d3a6beb4f38a89ab30e52814/PLMvZuPkQX.gif)

**Rupees**

There are two types of rupees.

* * When it spawns, it flashes quickly for a very very short time, it then changes to the Idle Animation.
* 1 Value Rupee
  * Increases player's rupees by 1.
  * The Idle Animation is flashing between blue and orange.
* 5 Value Rupee
  * Increases player's rupees by 5.
  * Doesn't have an idle animation, it's just the blue rupee sprite.
* If it's not collected until X amount of time, it will disappear.

**Differences**

* Orange Rupee \(Worth 1\)

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/ca555ae23bfdd9a0ae76fbd6286c426d/opIb8tpwlj.gif)

* Blue Rupee \(Worth 5\)

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/ce986861df7d950db3d49d061cb6c440/cf6xu75pWT.gif)

### **Enemies**

This section will now analyze the enemies as components as well.

* Every enemy that collides with Link will make him take damage.

**Octoroks**

These are the first enemies the player will encounter, they just wander around the room, they are not actively trying to find Link.

* They stop moving \(but the animation doesn't change\) before they shoot the projectile
* They shoot the projectile even if they are seeing Link
* If the projectile hits Link, he will take damage.
  * The projectile gets destroyed if it collides with walls.
  * Link's shield can block this projectile
* They collide with tiles. They are solid.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/a82ec800f4d3fa4426ad2d203634a815/xW4Ow65BSl.gif)

There's also Blue Octoroks, have more health than the red ones.

**Tektites**

These enemies just move in a very weird and unpredictable pattern. They move have a Parabolic movement. They probably choose a point where they want to land and then a parabola pattern is created to move to that point.

* Ignore map collisions completelty.
* From what we can see on the GIF they are not actively looking for Link
* They have an Idle animation, and when they jump they always have a "falling" sprite, which is the second sprite from the idle animation.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/51ffc0feaa9fb096ff5525d0a7816817/71VhRDpvVO.gif)

They also come in blue and red. The wiki claims that red ones jump more than the blue ones and both have the same health. And they have more chances to drop rupees and the clock treasure, I'd assume blue ones are the ones that have bigger loot change.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/51ffc0feaa9fb096ff5525d0a7816817/71VhRDpvVO.gif)

**Leevers**

These are enemies that spawn from the ground. Just like the previous ones, they are two kinds, a red one and a blue one.s

* They have an spawn animation, making you think that they actually come from the ground.
* Both red and blue will go back to the ground after a while.
  * They are invulnerable when on burrowed.
* Red Leevers are actively trying to find Link, once they spawn they will target Link's direction.
* When they hit Link, they go back to the opposite direction

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/9ff1b2e6c7d210504a567d2ac53acb29/RNWwTfVTAB.gif)

* Blue Leevers have a random pattern, they just simple don't mind Link at all.
* Blue leevers have more health than the red ones.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/beefdf8c2f9a62d1aaf5bea163b3a5cc/Leevers.gif)

**Peahats**

* They also ignore collisions
* Are semi-actively looking for Link
* They are invincible until they stand still \(they supposedly to be flying\), meaning they are on ground.
* They have a wind-up animation, that makes them feel like they are starting to move.
  * They move a bit slower during this time
* They slow down when they prepare to ground.
  * Their movement animation also slows down.
* The movement animation is just 2 frames.
* They can move diagonally, and it seems they try to do a circle pattern, surrounding Link.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/2236aad312d9fd12eb8684ba078d7845/vVekStVDeT.gif)

**Moblins**

* Very similar to Octoroks
* They collide with things
* They shoot Arrows, rather than rocks.
* Blue Moblins have more health

**Armos**

* They start immobile
* Start moving when collides with them.
* They have different movement speeds
* They collide with the room.
* Not actively Looking for Link
* They always start moving south.
  * Meaning, that Link will immediatly take damage if he collides with them from below.
  * If Armos is facing south, Link can collide from North and not take damage.
* They have a sprite when they move north.

**Ghinis**

These are very interesting. They only appear on the cementery. When you enter the room, there's only one Ghini there.

* Like an Armos, if you touch a stone, a Ghini will spawn.
* Like an Armos, after spawning, they start moving south first, then they change their direction.
* It has a lot of health.
* The Spawned Ghinis are invincible
* The only way you can defeat the other Ghinis is by keeping track of the "Original Ghini" and defeat him.
* The "Original Ghini" DOESN'T IGNORE COLLISIONS
* Interestly enough, when you kill the Main Ghini, the other spawned Ghinis will be defeated INSTANTLY, they can drop stuff as well.
* Spawned Ghinis ignore collisions
* Spawned Ghinis can move diagonally
* Ghinis can keep spawning, even if you have killed the "Main" Ghini.
* If you manage to get a clock, you can see that you they can spawn and they won't move, as mentioned before, you can't kill them, since you defeated the Main Ghini.
* The following image makes me wonder that the limit of enemies on a room is 11.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/5b1f37004f59ee9b6091eb0fc3454659/image.png)

**Lynels**

If you played Zelda Breath of the Wild, you might remember the big horse-lion enemy, well, this is the actual game where they appear first.

* They seem to be the same enemy behaviour like the Octoroks and the Moblins.
* They have more health.
* High chances to attack when it stops moving
* Only the Magical Shield can stop the sword projectile
* Their projectile hits a lot more. 
* Very poorly looking for Link

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/d75f6a110a7620fe8a3c5fdfc93f7a7c/JfHXmEZHwM.gif)

**Zola or Zora**

* Spawns from a \(apparently\) a random water tile.
* It shoots a projectile directly to Link. Simple angle between Zora's position and Link's position.
* The projectile has an animation
* Could it be that those projectile that it miss, are predictions on where he's going to move?

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/64972623ec4f5e2d3808501b9f07db8b/FpdNHXiUTY.gif)

**Rocks**

While they are not enemies since they cannot be defeated, we will put them at the very end of the overworld enemies since they are entities that need to be programmed.

* They seem to appear in X=Random,Y=0.
* They do a diagonal movement.
* Are always looking for Link
* They seem to change direction every time they make a move. \(1 diagonal movement\)

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/15787e0774104d8b407cc044b31104ae/GpkNy0ev1o.gif)

#### The Dungeon/Underground Enemies

These enemies only appear inside certain dungeons and not on the Overworld.

**Zol and Gel**

* They seem to work similar to many enemies that have the "roaming" behaviour.
  * Like the Octoroks, Moblins, Lynels
* When you kill a Zol, 2 Gels will spawn.    
  * Killing a Zol with a "strong weapon" will not spawn anything.
* Gels cannot drop anything, it's pretty useless to kill 'em.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/594cee18cc9d03e18734f202466d9d05/zola_ang_gel.gif)

**Rope**

* They slowly roam
* If Link its on their X or Y coordinate, they will charge to him.
  * Untl they collide with a wall

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/37bc14afd778c7d343ee96b478b34783/Rope.gif)

**Keese**

* Very similar to Peahats as a behaviour
* They speed up and move in circles
* They stop after a while
* Can be hit at any time
* 2 frame animation that speeds up

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/93f5fafcf6a65122510a97fb5d5308b2/keese.gif)

**Vire**

* Seem to have the wander behaviour that has been describen previously.
* They only jump when they move horizontally
* If you defeat them with a weak weapon, they will spawn keeses
* They cannot jump obstacles

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/ad79c01d3ded05178b4b38a52f9aeaa7/Vires.gif)

**Stalfos**

* Simple wander behaviour. As mentioned before
* Mirror walking animation
* Only damage Link with collision

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/9a9c07bc46e66a7c60dc5313a5890c66/stalfos.gif)

**Wall Master**

* These enemies seem to only appear on the edge of the map. As the name indicates, they come from walls.
* They seem to store Link current's position when they spawn and move to that position. They are not chasing him constantly. They have a programmed path
  * Required to programm that movement
* When collide with Link, he will take damage, and then it will be transported to the entrance of the dungeon.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/99adfd2ceb876696d21958246a4b761e/wall_master.gif)

**Goriya**

* Similar to many other more, has a simple roam pattern.
* Instead of shooting arrows or other known projectiles, they shoot the `Boomerang`
  * Like other enemies, they stop before shooting the projectile

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/7e21912fa2885301eff7db0cc9c83a2a/goriya.gif)

**Wizrobes**

**Orange Wizrobe**

* After some time, these will appear at the same X or Y coordinate than Link.
  * If there are 2 orange, chances are high that one will be at X and the other at Y.
  * It is possible to be both on X, or both on Y.
* They have a small invincivility time gap.
  * You can hurt them after that
* After appearing, they will shoot a projectile

**Blue Wizrobe**

* These are roaming like other enemies, not very actively looking for Link.
  * But then they decide to make a "warp" to another location.
    * During this time they are invicinble.
    * This warp can help them ignore obstacles, as they can just pass them through.
* If they match Link' X or Y coordinate they will shoot a projectile.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/6bdd597b797f96db490a2620aabaedda/wizrobe.gif)

**Darknut**

* Similar roaming behaviour as mentioned before.
* Blue Darknuts have more health.
* You can only hit a Darknut with your sword if you hit on their side or back, not in front of them. The shield blocks your attacks.
* Bombs are very useful, they hit no matter the side.
* They are like enemies that want to make you feel they are unstoppable.
* They dont appear to have knockback. Can really confirm with my game because I already got the strongest sword.
* Just a reminder than most enemies just have 2 frame animations.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/a3e8bb9b13914eb4aa2433ee39fe39d6/darknut.gif)

**Pols Voice**

* Roaming with extra behaviours.
  * They can jump horizontally
  * They can jump vertically
  * These jumps can jump obstacles. And they will jump whenever they find one.
  * They jump 2 tiles.
  * If they jump on another obstacle, they will jump again and so on.
* It takes a lot of hits to defeat.
* Inmune to bombs
* Arrows can defeat them in one hit
* They hit very hard.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/8d831ff410875ab3b6aab2904c0f0a82/VY740XHXTQ.gif)

**Lanmola**

* Worms that seem to follow the roaming algorithm mentioned before
* Blue ones are very very fast
* When they move, their attached body parts follow the head. Apparently they have 4 parts and the head.
  * This gives the illusion of complex movement.
* When you hit them, their body parts are destroyed.
  * Once all of them are destroyed, the head will continue moving, so you justs have to defeat the head to completely defeat them.
* They dont seem to have any kind of knockback or staggering. They keep moving even if you hit.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/fc0c078b2557990a429c775d01f42b5b/lanmola.gif)

**Like Like**

* Simple roaming behaviour.
* When they collide with Link, they will eat him.
  * When Link is inside, Link can't move.
  * You can use your sword while inside them, you can defeat them this way.
  * If Link has the Magical Shield \(Shield Lv. 2\) this enemy will eat it and you have to get a new one.
    * It's not immediate, but it takes a bit for them to eat it.
  * From what I can gather, Link is immune to other sources of damage when inside this enemy.
  * You can hit other enemies even if you are inside, sword collisions keep working, you can use your treasures too.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/b1a40650860a3558a0ea964654f40b4a/like_like.gif)

**Gibdo**

* They seem to be a copy paste of the Stalfos.
* Have more health than stalfos, so you could say these are the "blue stalfos".

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/e61e63814d53411b4de854c5d22bd802/gibdo.gif)

**Moldorm**

* A worm enemy, very very similar to Lanmola.
* This enemy can move diagonally. Biggest difference
  * Plus not that fast and it's easier to evade.
* It doesn't stagger or have knockback.
* Parts follow the head,  you can only know which part its the head by following their movement. The one leading its the head.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/fbc7134c61981c77c122a894ec186b6d/moldorm.gif)

**Bubble**

* I consider this enemies more like obstacles.
* You cannot defeat them.
* If you collide with them, they will "curse" you.
  * This is, Link can't use his sword.
* Medium fast roaming behaviour.
  * Seem to like to collide with something to change direction.
  * Not neccesarily need to collide to change direction.
* They don't do any damage.
  * There's a hit animation for Link, and you can use this time to make yourself invincible while the animation lasts.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/9172cc415c0a5952a51dfc9f4e684e28/bubble.gif)

**Trap**

* Obstacles that are just waiting for Link
* They come in pairs.
* 3 states
  * Idle state. Not moving at all.
    * When they match Link's X or Y coordinate, they will charge to that position, going to attack state.
  * Attack state.
    * When they collide with another trap, they will go to the "return state".
  * Return state
    * Slowly go back to their original position.
    * During this time, they will not charge at Link.
    * When back in original position they will go to Idle state.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/a92f90599c65aaf504a4386288318d89/traps.gif)

**Patra**

* It's considered a mini boss.
* An enemy that has 8 small patras rotating around him.
* It's invincible during this time.
* Blue patra moves very slowly.
* It flies, so it ignores collisions.
* You have to defeat the 8 parts to be able to attack the blue patra.
* They have a circle behaviour.
  * It can change the radious where it rotates around the blue patra.
* It doesn't stagger/knockback.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/58606e8d3f6c219f05e1d3d0ae0385bf/image.png)

### Bosses

* Bosses drop a Heart Container when defeated on a specific position on the room.
* Bosses can drop ruppes and other items too.

**Aquamentus**

* Moves very slowly.
* Moves only horizontally
  * Moves only in 3 tiles
    * This is, from mid goes to the right.
    * From right, to left, or mid. And so on.
* You can only hit the head.
* When hit, it will flash to orange.
* Body and head are separated animations from what I can see.
* Intervals to shoot 3 projectiles.
  * These seem to store Link's current position.
  * Link can evade them after they are launched to a predictable location.
  * These projectiles change animation after certain distance.

**Dodongo**

* This boss seems to have a simple enemy movement behaviour.
* Simple roaming.
* Can only be defeated by making it eat a bomb.
* After eating a bomb, it will have a "hurt" animation. Sprite changes to its body exploding from inside.
* Takes 2 bombs to defeat it.
  * It continues walking after the first hit.
  * Flashes when its defeated.
* Immune to all damage, except bombs.

![](https://trello-attachments.s3.amazonaws.com/5b74b9cba4c5e76a79ed93c5/5cb6560482f83b45c11ed36e/e0c7385d0aa85393238969a7262dfb0e/dodongo.gif)

**Manhandla**

* Big enemy.
* Made of 5 parts.
  * Center and 4 cardinal directions. Cardinal directions are pincers.
  * Pincers have their own idle animation.
* You can only hit the pincers.
* You defeat it when you destroy the 4 pincers.
* Every time you destroy a pincer, it will move faster.
* Each pincer can shoot a projectile. It's quick and it shoots to Link's current location.
  * No feedback to know when it's going to shoot.
* I'd love to describe it as a ping pong movement. But it's not always like that, seems like a combinationn of ping pong / bounce with the the roaming behaviour for other enemies.
  * The fact that this enemy is very big, made of various parts and that every time you destroy a pincer it moves fast, makes you think that it could have a very different movement algorithm.
  * Biggest difference I see is that it "bounces" when it collides walls.

**Gleeok**

* Just like Aquamentus it's a "horizontal" fight, Gleeok's battle is a vertical fight, it has the advantage in vertical directions.
* Made of 2 or 3 heads, and its body.
  * Body doesnt move.
  * Only heads/neck move.
* To defeat him, you have to defeat their heads.
  * When you defeat a head it detach and have it's own red sprite.
  * Detached heads seem to have the Manhandla move pattern.
  * Detached heads can shoot projectiles
  * Detached heads are invincible. You have to defeat every attached head.
* Attached/undefeated heads move diagonally \(pretty much the neck it's the one that moves\). Yet they seem to also be made of small parts from the neck, neck parts seem to follow the head. 
  * These heads also shoot projectiles.

**Digdogger**

* An invincible enemy.
  * Unless you play the Recorder
  * When the recorder is played, the big Digdogger will be destroyed.
    * It will then spawn up to 3 mini Digdoggers.
    * Mini Digdoggers are slighly faster.
    * They seem to have the same movement behaviour than the big one.
    * Apparently, when you hit them, they will increase their speed.
    * Can't stagger or have any knockback.
* The big Digdogger moves very slowly.
* Seems to have the simple roaming behaviour with diagonal movement.
* It is flying, so it ignores collisions.

**Gohma**

* Moves horizontally and vertically. 
* Seems to evade collisions, it tries to not touch collisions, it changes direction before even colliding with something.
* Can't move diagonally.
* Invincible to everything.
* It has its eye closed, but after some time, it will open it.
* When the eye is open, you can shoot an arrow to damage it and be able to defeat it.
* Shoots projectiles.
  * From 2 places, their legs. Right and Left legs.
  * Doesn't shoot from the eye.

**Ganon**

* Very cheater. It feels very cheap, and because of this, it's very hard.
* Ganon is made up of 4 tiles.
* Invisible the whole time.
* It has V, or U pattern.
* It has ceirtain points on the map where it will "appear". But still, it's invincible.
* The player has to "guess" where Ganon will appear.
* Ganon hits INSANELY hard. It can hit the player if the player collides with Ganon at the position where it "appeared". This is, not just Ganon's projectiles can hurt Link.
* When hit, it's hurt sprite will appear, feedbacking the player, it then goes invisible again.
* From what I can gather, it shoots a projectile from the last position it "appeared".
* After many hits, Ganon will change to a orange/brown sprite.
  * This means you can finally defeat him when this orange/brown Ganon appears.
  * You defeat him by shooting ONLY a Silver Arrow.
  * If you don't hit him with the arrows, it will go back to it's usual behaviour. The player has to hit it once again and make the orange/brown sprite appear and try to shoot an arrow.
  * Once defeated...
    * It will trigger a death animation.
    * It will spawn a triforce shard, presumably the triforce of power.
    * It will spawn his remnants, a red powder/ashes.
    * When grabbing the triforce, it will play a flash animation, feedbacking that you got it and you can finally proceed to the next room. 

### The End

For now that's what I'm covering up. To summarize, we saw.

* Game Screens
  * Menus
* Collisions
  * Used by the player, treasures and enemies.
* Player's Movement
* Items / Treasures
* Enemies

We analized how they could be working internally. And I just want to remind you how many things are getting recyled here.

* Many enemy behaviours are similar.
  * Some differ in different move speeds
  * Different health
  * Different damage they do
  * They all have the same death animation
  * Some can move diagonally
  * Some can ignore collisions \(fly\)
* There's a base collision detection that every entity uses.
* Many items, like projectiles use recycled code.
  * Projectiles are used by both the player and enemies.

I hope this is not just useful for me, since this document was made for the R&D work I'm doing. But also it can be useful to others.

~ Thanks so much, this was me, Alex, with another document/essay of Game design. 😊

