# Inventory

An `Inventory` is a collection of `Items`, this system is used to store the items a player has. The inventory has a small dependency with your Items, because depending on how you define your `Item` model, it will the internal functionality.

## Functions

* `Add(item,quantity)`
  * Eg. `Add(Red Potion, 2)`
    * This means you will put 2 Red Potions to the inventory.
* `Remove(item,quantity)`
  * Removes item's quantity from the inventory.
* `Find(item)`
  * Retrieves the item needed from the inventory.

