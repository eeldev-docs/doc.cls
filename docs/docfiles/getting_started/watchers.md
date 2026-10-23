---
sidebar_position: 4
description: Add your own objects as Watchers that can trigger the loading screen.
---

# Watchers

Add your own Watcher objects to trigger the loading screen from objects that the plugin does not ask by default, for example an Actor in the level.

## Using an Actor
In this example we use a simple Actor Blueprint that asks the game to display the loading screen. We add the Loading Process Interface to the Actor Blueprint, and add the Actor as a watcher with **Add Loading Screen Watcher**.

### Setting up the Actor
![Adding the Actor as a watcher](/img/my-actor-1.png)

If **Should Show Loading Screen** returns true, the loading screen is displayed as soon as this Actor is spawned.

![Should Show Loading Screen returns true](/img/my-actor-2.png)

The function doesn't have to return true all the time. Use a bool to decide when the loading screen should be visible.

### Limit Loading Screen Duration
This shows the loading screen for 4 seconds only.

![Set the bool after a delay](/img/my-actor-4.png)

![Return the bool](/img/my-actor-3.png)

## Removing a Watcher
Call **Remove Loading Screen Watcher** when the object should no longer be asked. Destroyed objects are removed automatically.

:::info
Watchers are held weakly. Adding a watcher does not keep the object alive.
:::
