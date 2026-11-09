---
sidebar_position: 2
description: All Blueprint nodes, events and interfaces in the CommonLoadingScreen plugin.
---

# Blueprint Nodes

## Loading Screen Manager
Get it with the **Loading Screen Manager** node, which is a Game Instance Subsystem getter. It doesn't exist on a dedicated server.

### Functions
| Node | Description |
|---|---|
| Get Loading Screen Display Status | True while the loading screen is shown. |
| Get Loading Progress | How far the loading has come, from `0` to `1`, or `-1` if nothing reports progress. See [Loading Progress](/docfiles/getting_started/progress). |
| Get Debug Reason for Showing or Hiding Loading Screen | Why the loading screen is shown or hidden. See [Displaying Reason](/docfiles/getting_started/reason). |
| Get Loading Screen Custom Text | The custom text as a string. |
| Get Loading Screen Custom Display Text | The custom text as a localizable text. Pure node. |
| Get Current Loading Map | The name of the map that is loading, or was loaded last. |
| Get Current Loading Screen Tip | The tip to show. Pure node. See [Tips](/docfiles/getting_started/tips-slideshow-music#tips). |
| Get Loading Screen Status Text | The text to show the player. Pure node. See [Status Text](/docfiles/getting_started/reason#status-text). |
| Set Loading Screen Tips | Replaces the tips while the game runs. See [Changing tips and images](/docfiles/getting_started/tips-slideshow-music#changing-tips-and-images-while-the-game-runs). |
| Clear Loading Screen Tips | Goes back to the tips from the settings. |
| Set Loading Screen Images | Replaces the images from the next loading screen. |
| Clear Loading Screen Images | Goes back to the images from the settings. |
| Is Waiting For Key Press | True while the loading screen waits for a key press. Pure node. See [Waiting for a key press](/docfiles/concepts/how-it-works#waiting-for-a-key-press). |
| Continue From Loading Screen | Stops waiting for a key press. |
| Is Loading Screen Fading Out | True while the widget fades out after the loading screen was hidden. Pure node. See [Fading out](/docfiles/concepts/how-it-works#fading-out). |
| Add Loading Screen Watcher | Adds an object that is asked whether the loading screen should be shown. See [Watchers](/docfiles/getting_started/watchers). |
| Remove Loading Screen Watcher | Removes a watcher. |
| Set Loading Screen Custom Text | Sets a text that your widget can show. Takes a world context, so it can be called from anywhere without the manager. |
| Set Loading Screen Custom Display Text | Same as **Set Loading Screen Custom Text**, but takes a localizable text. |

### Events
Bind these on the Loading Screen Manager.

| Event | Parameter | Description |
|---|---|---|
| On Loading Screen Visibility Changed Delegate | `New State` | The loading screen was shown (`true`) or hidden (`false`). |
| On Show Loading Screen Additional Secs Triggered | `Is Active` | The extra hold time started (`true`), or the loading screen was hidden (`false`). |
| On Pre Load Map Triggered | `Map Name` | A map started loading. |
| On Post Load Map Triggered | | A map finished loading. |
| On Seamless Travel Start | `Map Name` | Seamless travel started. |
| On Loading Screen Tip Changed | `Tip` | A new tip was selected. See [Tips](/docfiles/getting_started/tips-slideshow-music#tips). |
| On Loading Screen Status Text Changed | `Status Text` | The status text changed. |
| On Waiting For Key Press Changed | `Is Waiting` | The loading screen started (`true`) or stopped (`false`) waiting for a key press. |
| On Loading Progress Changed | `Progress` | The loading progress changed. See [Loading Progress](/docfiles/getting_started/progress). |

## Loading Process Task
Shows the loading screen on demand. See [Show on Demand](/docfiles/getting_started/on-demand).

| Node | Description |
|---|---|
| Create Loading Screen Process Task | Creates a task and shows the loading screen with the given reason. Returns the task. The advanced pins **Timeout Seconds** and **Unregister With Context Object** make the task stop by itself. |
| Unregister | Removes the task, so it no longer keeps the loading screen up. |
| Set Show Loading Screen Reason | Changes the reason of the task. |
| Get Show Loading Screen Reason | The reason of the task. Pure node. |
| Set Progress | Reports how far the task has come, from `0` to `1`. See [Loading Progress](/docfiles/getting_started/progress). |
| Set Status Text | Sets a text to show the player. See [Status Text](/docfiles/getting_started/reason#status-text). |
| Is Expired | True when the task has timed out, or its context object is gone. Pure node. |

## Loading Process Interface
Implement it on the Game State, a Player Controller, one of their components or a [Watcher](/docfiles/getting_started/watchers).

| Function | Description |
|---|---|
| Should Show Loading Screen | Return true to show the loading screen. Set **Out Debug Reason** to say why. |
| Get Loading Progress | Return true and set **Out Progress** to a value from `0` to `1` to report progress. Return false to not be counted. |
| Get Loading Status Text | Return true and set **Out Status Text** to report a text to show the player. |
