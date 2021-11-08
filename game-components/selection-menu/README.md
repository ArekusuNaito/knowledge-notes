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

That is our simplest way to describe it, and there's many ways on how we can define these actions.

## Components

* The list of things in the menu. Normally a set of images or text.
* The associated action to the menu, that way we know that to certain item is linked to a certain action.

