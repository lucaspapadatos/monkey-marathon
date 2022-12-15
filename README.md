![Banner](https://github.com/lucaspapadatos/monkey-marathon/blob/main/readme%20images/226banner.png)
PLAY HERE: https://creative.caslab.queensu.ca/~GDP9/
:-
GAMEPLAY: https://www.youtube.com/watch?v=x4vsoj9cuk4
## Summary
“Monkey Marathon” is a top-down shooter with progression upgrades, where the player’s objective is to travel as far as possible while killing or avoiding guards that are trying to stop the player. The map is procedurally generated with checkpoints along the way, with guards getting more difficult after every checkpoint to scale with the player’s upgrades. 

Regarding progress thus far, we have already implemented basic player movement and shooting mechanics, functioning guards (and basic guard AI), random level generation, a fully functioning store (with upgrades affecting the game), an economy (including sources and sinks), and the ability for players to save their progress. We have yet to implement gold coin spawning, the slingshot weapon/tool (makes a sound to distract guards), final sprites and animations, menu/settings UI, sound effects, minor store changes, and major balance changes, as well as fixing various bugs discovered in playtesting. There are also some optional features that we would like to implement if time permits, but aren’t necessary for the initial release. These include more advanced map generation (ability to generate more complicated maps), more advanced guard AI (to make guards more “life-like”), ultimates, blockades, throwable explosives, lockers for the player to hide in, and laser-sights.

Currently, the greatest challenges in development are balancing the game, scaling the difficulty as the game progresses, as well as implementing the algorithms associated with advanced map generation and advanced guard AI.

In terms of playtesting, the developers have been constantly playtesting throughout development to make sure everything works, however the most beneficial playtesting we’ve done so far is 2 separate rounds of playtesting with the same non-developer playtesters. They provided crucial feedback regarding the player experience, especially in terms of what needed to be balanced. Furthermore, they noticed several bugs and exploits that need to be fixed. The most important feedback revolves around the game being too easy, including the ability to take advantage of guard AI, overpowered strategies, and the player being too economically rich. All feedback has either already been addressed/fixed, is planned to be fixed, or is still being considered. 

## Gameplay Overview
“Monkey Marathon” is best described as a top-down shooter with infinite level generation and progression upgrades. Our game has no specific target audience and should be playable for everyone. In this game, you will play as a monkey who is trying to escape a laboratory where the monkey has been experimented on. Starting from the bottom floor of the laboratory, the monkey’s goal is to reach the roof to escape.  However, in the actual gameplay, there are infinite floors the player can traverse and never reach the roof. Regardless, the player’s goal is to run as far as possible while having to fight or sneak past guards trying to stop them. Throughout their play-through, the player will earn gold from collecting it throughout the map, as well as earning it based on the distance the player has traveled in a “run”. When the player dies, they will have the option of using this gold to purchase upgrades from the store to help them progress further on their next run. The stronger the player gets with upgrades purchased, the farther they will be able to run, and they will encounter stronger and greater numbers of guards. When the player reaches the staircase going up to the next floor, this will act as a checkpoint, so the player will now respawn on this new floor when they die.

![capture1](https://github.com/lucaspapadatos/monkey-marathon/blob/main/readme%20images/capture1.PNG)

## Core Design Features
In this game, you will play as a monkey. Players will move their character using standard WASD movement controls. By default, they will be sprinting but players have the option to hold the shift key to sneak instead, which will prevent the player from making noise while moving, which the guards can hear. You can also aim and shoot by pointing and clicking the mouse. Players can toggle through their weapons by looking at the hotbar and pressing the number keys for the appropriate weapons. The monkey will have a health bar above its sprite. When a player is hit by an enemy, they will have damage inflicted on their health. If their health bar reaches zero, their run is over.

Random map generation is one of our novel features. Once you begin playing our game, a map is randomly generated using a series of hallway blocks. These blocks are all of the same sizes and each has openings in two directions.

![capture2](https://github.com/lucaspapadatos/monkey-marathon/blob/main/readme%20images/capture2.PNG)

The player spawns at the entrance of the floor, at the bottom of the map to reach the exit at the top. Each tile that is placed during map generation has a chance of spawning gold and/or a guard. Every time a player reaches the end of the floor, a new map is generated with higher chances of spawning guards, and with more difficult guards. Having these infinite randomly generated maps allows for a unique experience for the player every time they play.

![capture3](https://github.com/lucaspapadatos/monkey-marathon/blob/main/readme%20images/capture3.PNG)

The main obstacle in your way is guards. There are three different types of guards. The first is the white guard who only has a melee attack but moves faster than the rest of the guards. Next, there is the blue guard, who has a ranged pistol attack. Finally, there is the green guard, who has more health than the blue guard and carries an assault rifle, although they may move slower, depending on balance testing. 

![capture4](https://github.com/lucaspapadatos/monkey-marathon/blob/main/readme%20images/capture4.PNG)

A guard can exist on the map in three different states. Each guard has a cone of vision in front of them and a hearing radius around them that affects their states. When spawned, they are in a patrol state in which they will either move back and forth between two different tiles on the map or stay stationary at one point. If the player ever enters the guard's cone of vision, they will enter the pursuit state in which they will either chase the monkey or stop and attack it if the player is within range. If the guard loses sight of the monkey, they will enter an investigation state. If the guard hears something (the player running, shooting, or the slingshot weapon), they will also enter an investigation state. In this investigation state, they will travel to the last point they saw the monkey, or the position they heard the sound, check the area, and if they find nothing they will go back to their patrol state.

Throughout your playthrough, you will earn gold by picking it up off the ground throughout the laboratory. You will additionally earn gold every time you die based on distance traveled throughout the run. Your gold is saved after every run and can be used to purchase items from the store.

Every time the player dies or launches the game, they will enter the store. Here, they can spend gold to increase their stats, unlock new weapons and upgrade their weapons. The player stats that can be upgraded are: health, sprint speed, and sneak speed. The prices will start pretty low but gradually increase as you buy upgrades. The weapons available for purchase are: a pistol, slingshot, shotgun, and assault rifle. For each weapon, the player can upgrade the ammo and weapon damage. The player can also buy a silencer exclusive to the pistol.

![capture5](https://github.com/lucaspapadatos/monkey-marathon/blob/main/readme%20images/capture5.PNG)

Each run, you will start with a certain amount of ammo for each gun you own. After you run out of ammo for a specific gun, you won’t be able to use it anymore for the rest of the run. If you have a silencer for the pistol, gunshots cannot be heard even within a guard's hearing radius.

There are currently four weapons in the game. First, there is the pistol, the only weapon you start with, it shoots at a low rate and does minimal damage. Next, there is the slingshot, this weapon is very different from the others as instead of shooting it at guards, you shoot it at walls to create a sound which will attract guards to that location to investigate, clearing a way for the player to sneak past.. Additionally, there is the shotgun which shoots multiple bullets at once, dealing massive damage to enemies, however it is only good at short range, as bullets despawn after a fixed distance Lastly, there is an assault rifle that inflicts more damage than a pistol while shooting at a faster rate.

In this game, you will have the option of playing with two different play styles depending on the situation and preference: stealthy or loud and proud. For instance, if you want to play stealthy, you can focus on purchasing upgrades like the slingshot, pistol with a silencer, and sneak speed. On the other hand, if you wish to play aggressively and shoot your way out, you can invest your gold in increasing health, ammo, damage, and big guns. Players can freely switch between these playstyles, but the player’s previous upgrades might not be relevant to the new playstyle. 

![capture6](https://github.com/lucaspapadatos/monkey-marathon/blob/main/readme%20images/capture6.PNG)

# Instructions
We have added a button in the menu screen called “How To Play” which provides the player with instructions on how to play the game. Please look there for detailed instructions regarding our game. We have also decided to leave in the following developer commands in-order for the grader to reach higher levels of the game a lot faster than in a normal playthrough:
- 1-4: switch to pistol, slingshot, shotgun, and AR (assuming the weapon has been purchased in the store)
- Numpad 0-2: switch floor level to 0, 7, and 15 respectively. Note that the change will only take effect on the next generated map.
- delete: kills yourself (easiest way to exit to store/main menu)
- G: adds $100 when in game scene (can click multiple times)

## Contribution
- Wrote Novelty portion of game proposal
- Added pictures and formatted game proposal
- Voiceover for the video demo
- Wrote Playtesting portion of the progress report
- Added pictures and formatted playtesting and progress report
- Found music for the store and gameplay in-game
- Filled out creative computing show form which includes the banner and video as well as originally uploading the game to the caslab servers
- Added polygon collider to the monkey
- Created the GuardBullet script based off of the original bullet script
- Made the guard aimbot to shoot in the direction of the monkey
- Made monkey take damage when guard bullet collides with the monkey
- Implemented original sneaking movement when holding shift
- Created the first/basic version of the green guard script and green guard prefab
- Created the first/basic version of the white guard script and white guard prefab
- Did a rough implementation of the white guards melee attack where the white guard will shoot the monkey at a very close range (no longer in game)
- Roughly implemented the distance traveled using a function that takes the distance the monkey has moved from his start position and dividing it by 10 (no longer in game)
- Created the distance traveled text at the top right of the screen which updates every frame
- Implemented health bars on blue, green, and white guards
- Created ScreenOverlayCanvas with distance traveled and gold count texts displaying on screen
- Created gold coin prefab
- Made gold count increment when monkey collides with gold coin on the floor
- Made player and guard bullets ignore collision with gold coins on the floor
- Revamped distance traveled to increase when the monkey collides with the map chunk. The collider is disabled upon impact to avoid incrementing distance traveled for previously visited map chunks.
- Added a global light to all game objects except for the monkey and gold coins
- Implemented guard flashlights (field of vision cones) and created polygon collider of the same size to detect when monkey is in the guards field of vision
- Created “noise” prefab (a circle displaying the area the sound reaches)
- Instantiated “noise” when slingshot rock collides, monkey fires a weapon, and monkey sprints
- Made “noise” deactivate when the pistol is shot and the silencer is purchased
- Made noise circle delete after 0.1 seconds upon being created in level
- Created setIntriguePoint function in all guards scripts that sets guards state to investigative and changes guard path to location of the where the noise was
- Polished noise circle by disabling the sprite when the monkey is sneaking
- Updated setIntriguePointfunction for all guards by using investigative state variables
- Resized guards field of vision colliders to align with guard flashlights as before
- Made upgrade prices increase when upgrade has been purchased once
- Added upgrade prices to the save file so they will be there the next time the player enters the store
- Made upgrade prices reset to base values when player resets stats
