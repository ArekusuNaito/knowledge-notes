A `Bakery` is a system that given a `Recipe` it will remove the items required in the recipe from an inventory and it will award the recipe items an inventory.

## Example

The player wants to make the following Item. `Red Potion`. And the recipe looks like this.

```js
{
  requires:[Red Herb x5, Empty Bottle x1],
  awards: [Red Potion x1]
}
```
If the player is holding those items, then it will be able to receive a Red Potion.


### Functions
- `Create(recipe,inventory)`
  - Takes the required items indicated by the recipe and it will award you with the ones indicated by the recipe.
  - This function will mutate the inventory.
- `CreateAfter(recipe,inventory,duration)`
  - Just like create, the added functionality is that it will create the item after the given duration (Eg. Create this, after X seconds)
- `CreateBatch(howMany,recipe,inventory)`
  - This function will call the Create function as many times as is specified. They will be created immediately.
- `CreateBatchAfter(howMany,recipe,inventory,timePeriod)`
  - This function will create as many recipe awards as specified, with the addition of being created after a time period. Eg. Create 5 Red Potions, but you want to wait a timePeriod in between those creations.
- CalculateHowManyCanBeCreated(recipe,inventory) 
