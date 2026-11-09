---
sidebar_position: 1
slug: /
description: CommonLoadingScreen is a loading screen system for Unreal Engine based on the Lyra loading screen, with splash screens, automatic level transitions and on-demand loading screens.
---

# Introduction

## The CommonLoadingScreen Plugin
The CommonLoadingScreen plugin (CLS) is an extension of the loading screen that was released with the Lyra demo for Unreal Engine 5. It also adds support for earlier Unreal Engine versions.

The plugin shows a loading screen automatically while the game is loading, and keeps it up until nothing in the game needs it anymore. Any object can ask for the loading screen by implementing the **Loading Process Interface**.

## Features
- **Splash screen on game startup**, shown before the engine has finished loading. Choose between a black screen, a loading text, an image or video, with an optional logo, tip, version and shader progress. See [Splash Screen](/docfiles/concepts/splash-screen).
- **Tips, an image slideshow and background music** without writing any code. See [Tips, Slideshow and Music](/docfiles/getting_started/tips-slideshow-music).
- **Automatic loading screens** when loading a level, during seamless travel and when connecting to a server. See [When the Loading Screen Is Shown](/docfiles/concepts/how-it-works).
- **A built-in loading screen** with ready-made layouts, spinners and color themes, so no widget is needed. See [Built-in Loading Screen](/docfiles/getting_started/built-in-loading-screen).
- **Your own UMG widget** as the loading screen, set in Project Settings. See [Using the Plugin](/docfiles/getting_started/using-plugin).
- **Keep the loading screen up from your own code** by implementing the Loading Process Interface on the Game State, Player Controller, their components or any [Watcher](/docfiles/getting_started/watchers).
- **Show it on demand** from any Blueprint with a world context. See [Show on Demand](/docfiles/getting_started/on-demand).
- **A reason for every loading screen**, which you can show in the widget or print to the log. See [Displaying Reason](/docfiles/getting_started/reason).
- **Extra hold time** after loading finishes, so texture streaming can catch up before the world becomes visible, and a **minimum display time** so short loads don't flicker.
- **Fade in and fade out** of the widget. See [Fading out](/docfiles/concepts/how-it-works#fading-out).
- **Press any key to continue** after a map has loaded. See [Waiting for a key press](/docfiles/concepts/how-it-works#waiting-for-a-key-press).
- **A different widget, movies, tips, images or music per map** with Map Overrides. See [Map Overrides](/docfiles/reference/settings#map-overrides).
- **Blocked maps** that never show a loading screen, such as a main menu level, also with seamless travel.
- **A status text for the player** that follows what the game is doing. See [Status Text](/docfiles/getting_started/reason#status-text).
- **Loading progress** for progress bars, with an event when it changes. See [Loading Progress](/docfiles/getting_started/progress).
- **An animated widget while a map loads**, drawn by the Movie Player. See [Keeping the widget animated](/docfiles/concepts/how-it-works#keeping-the-widget-animated-while-a-map-loads).
- Input is blocked while the loading screen is shown. The console still works in builds other than Shipping.

## Requirements
| | |
|---|---|
| Target platforms | Windows, Mac, Linux, Android, iOS |
| Dedicated servers | No loading screen is created on a dedicated server |
| Unreal Engine | See the [Fab listing](https://www.fab.com/listings/356807ad-0cb8-40a4-917a-fcf938637afb) for the supported engine versions |

## Where to go next
1. [Install the plugin](/docfiles/getting_started/installing-plugin)
2. [Configure it in Project Settings](/docfiles/getting_started/configuring-plugin)
3. [Create your loading screen widget](/docfiles/getting_started/using-plugin)
4. Read [When the Loading Screen Is Shown](/docfiles/concepts/how-it-works) to understand what keeps it up