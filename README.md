# doop-dungeon
> doop-dungeon stands for Dashou's Oriented Object Programming Dungeon
*Delve into a dungeon filled with enigmas, treasures and enemies !*
## Idea
Object Oriented Programming is possible in C ! I love this language so much that I wanted to make a small project
to show that it is more than usable in many situations where OOP is useful. Furthermore, I wanted to try my hand
at some GTK programming.

### Game
#### Window
A simple log window will show the events of the game as they arrive. Below, a row of buttons with the different
actions the player will be allowed to make. On the side, a panel showing the current inventory of the player.
#### World
The player will progress through a dungeon floor, encountering traps, enemies, treasures. Once the player
has walked enough steps in the dungeon, they reach a new floor, increasing the difficulty of the game.

A state machine will keep track of the current state of the world. Is the current state combat, 
exploring, dialogue ? etc...

#### Events
Events that happen during a turn will be queued (in a queue data structure) and dispatched each time
the current situation is updated.

For example, an enemy is attaked with a fireball spell. The events that will populate
the queue could look like this.

##### Event queue example
1. The fireball is cast
2. The enemy is hit
3. The hit was critical
4. The enemy dies
5. The enemy drops a health potion
6. Last enemy was killed, ending combat.

Each one will have its own parameters and be displayed in the correct order.

#### Entities
The player has a name, an inventory, health points, magic points.
The enemies have the same stats and also have an inventory.

#### Inventory
The player will be able to obtain 3 types of item.
- Key Items (Cannnot be directly used, are needed for progression)
- Consumable items (Have uses, can be used at anytime either during exploration or combat)
- Spells (Can be used in combat or exploration, costs magic to cast.)

Key items and spells would be statically defined as they do not need unique instances.
Consumables items would need heap allocation for each instance since they need to keep track
of the number of uses they have left.


