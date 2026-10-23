---
sidebar_position: 3
description: Create a loading screen widget and tell the loading screen when to show from the Game State.
---

# Using the Plugin

## Loading Screen Widget
- The loading screen can be as simple or as advanced as you want. In this example we use a simple widget with a black background and the text LOADING.

![Loading widget](/img/loading-widget.png)

- Create a loading screen widget and set it as the **Loading Screen Widget** in Project Settings.

![Set the widget in Project Settings](/img/widget.png)

## Automatic Loading Screen Events
The loading screen triggers automatically for these game events:

- Game startup (the [Splash Screen](/docfiles/concepts/splash-screen))
- Level switching and loading
- Seamless travel
- Connecting to a server

See [When the Loading Screen Is Shown](/docfiles/concepts/how-it-works) for the full list of checks.

## Custom Loading Screen Events
The plugin continuously asks commonly used objects whether it should display a loading screen. You can also add your own objects as [Watchers](/docfiles/getting_started/watchers).

### Commonly used objects
These objects are asked by default:

- Game State
- Game State Components
- Player Controller
- Player Controller Components

If any of them implements the **Loading Process Interface**, it can tell the game to display the loading screen.

## Game State Example
In this example we implement the Loading Process Interface in the Game State. Whenever **Should Show Loading Screen** returns true, the loading screen is displayed.

### Adding the Loading Process Interface
Open **Class Settings** and add **Loading Process Interface** under **Implemented Interfaces**.

![Adding the interface](/img/gamestate-1.png)

### Interface Added
![Interface added](/img/gamestate-2.png)

### Should Show Loading Screen
- If this function returns true, the loading screen is displayed until it returns false.
- Set **Out Debug Reason** to explain why. The reason is shown in the log and can be [displayed in your widget](/docfiles/getting_started/reason).

![Should Show Loading Screen](/img/gamestate-3.png)

:::info
**Should Show Loading Screen** is called every frame while the plugin checks for a loading screen, so keep it cheap.
:::
