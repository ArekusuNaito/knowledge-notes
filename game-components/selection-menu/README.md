---
description: >-
  A Menu is a list of things. Here we want to select something from the menu to
  be able to execute certain action.
---

# Selection Menu

## Data description

A way to describe this component is by having a group of items and an associated action.

```javascript
let menu = 
[
    { 
     "name":"New Game",
     "action":()=>{Screen.ChangeTo("NewGameScreen")}
    }
]
```

That is our simplest way to describe it, and there's many ways on how we can define these actions. In older games this selection menu was controlled with the default gamepad's input, the D-Pad and then an analog pad.

## Components

* The list of things in the menu. Normally a set of images or text.
* The associated action to the menu, that way we know that to certain item is linked to a certain action.
* Highlighted Item. This is, which of all the items is the one the player is currently selecting, which is not the same as submiting.
  * It is usually shown with a graphic cursor.
  * The graphic can also change to a highlighted version.

## Examples

### Final Fantasy Tactics Advance

{% embed url="https://youtu.be/HWQcjlkS5Qo" %}

### The Great Circus Mistery - SNES

{% embed url="https://youtu.be/u5s5xksLduw" %}

### Advance Wars

