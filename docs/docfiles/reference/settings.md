---
sidebar_position: 1
description: Every Project Setting and console variable of the CommonLoadingScreen plugin.
---

# Settings and Console Variables

The settings are in **Edit → Project Settings → Plugins → Common Loading Screen**, and are saved to `Config/DefaultGame.ini` under `[/Script/CommonLoadingSettings.CommonLoadingScreenSettings]`.

## Display
| Setting | Default | Description |
|---|---|---|
| Loading Screen Widget | None | The UMG widget shown as the loading screen. A throbber is shown if it can't be loaded. |
| Loading Screen ZOrder | `10000` | The Z order of the widget in the viewport. Keep it higher than your other widgets. |
| Splash Screen Type | `BLACK` | The [splash screen](/docfiles/concepts/splash-screen) on startup: `BLACK`, `LOADING`, `IMAGE` or `VIDEO`. |

## Configuration
| Setting | Default | Description |
|---|---|---|
| Disable Splash Loading Screen | Off | Turns off the splash screen. |
| Force Tick Loading Screen Even in Editor | On | Ticks Slate once when the loading screen is shown in the editor, so it is drawn right away. |
| Use Movie Player During Load Map | Off | Shows the widget with the Movie Player while a map loads, so it keeps animating. See [Keeping the widget animated](/docfiles/concepts/how-it-works#keeping-the-widget-animated-while-a-map-loads). |
| Show Loading Screen Additional Secs | `2.0` | Seconds to keep the loading screen up after loading has finished, so texture streaming can catch up. |
| Show Splash Screen Additional Secs | `2.0` | Seconds to keep the splash screen up after the engine has finished loading. |
| Loading Screen Heartbeat Hang Duration | `0.0` | Seconds the loading screen can be up before the game is considered hung. `0` turns it off. |
| Log Loading Screen Heartbeat Interval | `5.0` | Seconds between each log of what is keeping the loading screen up. `0` turns it off. |
| Blocked Map Names | Empty | Maps that never show a loading screen when loaded or travelled to, also with seamless travel, for example `MainMenu`. Use the map's asset name, not the full path. |

## Splash Screen Configuration
These settings are shown for the matching **Splash Screen Type**.

| Setting | Type | Default | Description |
|---|---|---|---|
| Splash Screen Image | `IMAGE` | Plugin default image | The Texture 2D to show. |
| Splash Screen Stretch | `IMAGE` | `Scale To Fit X` | How the image is scaled. |
| Splash Screen Stretch Direction | `IMAGE` | `Both` | Whether the image may be scaled up, down or both. |
| Splash Screen Loading Text | `LOADING` | `LOADING...` | The text to show. |
| Splash Screen Loading Font | `LOADING` | Regular, size 10 | The font of the text. |
| Splash Screen Movies | `VIDEO` | Empty | The movies to play on startup. See [Adding movies](#adding-movies). |
| Splash Screen Movie Playback Type | `VIDEO` | `Normal Playback` | `Normal Playback` plays the movies once, `Looped Playback` loops all of them and `Looped Last Playback` loops the last one. |
| Splash Screen Movies Are Skippable | `VIDEO` | On | The player can skip the movies with a key or mouse click. |
| Wait For Splash Screen Movies To Complete | `VIDEO` | On | Plays the movies to the end. When off, they stop as soon as the engine has finished loading. |

## Loading Screen Movies
| Setting | Default | Description |
|---|---|---|
| Loading Screen Movies | Empty | The movies to play while a map loads. See [Adding movies](#adding-movies). |
| Loading Screen Movie Playback Type | `Looped Last Playback` | `Normal Playback` plays the movies once, `Looped Playback` loops all of them and `Looped Last Playback` loops the last one. |
| Loading Screen Movies Are Skippable | Off | The player can skip the movies with a key or mouse click. |
| Wait For Loading Screen Movies To Complete | Off | Plays the movies to the end. When off, they stop as soon as the map has loaded. |
| Show Loading Screen Widget Over Movies | Off | Draws the **Loading Screen Widget** on top of the movies. |

### Adding movies
- Put the movie files in `/Content/Movies` in your project, for example `Content/Movies/MyMovie.mp4`.
- Enter only the file name, without the path or extension. For `Content/Movies/MyMovie.mp4` you enter `MyMovie`.
- A movie that can't be found is skipped and a warning is logged.
- Movies are not packaged as assets. Make sure they are copied to the packaged build: turn off **Skip Movies** and add the names to **Movies that are not in UFS** under **Project Settings → Packaging**. With **Use Zen Store** on, the movies end up in the pak file and the Movie Player can't open them.

## Debugging
| Setting | Default | Description |
|---|---|---|
| Log Loading Screen Reason Every Frame | Off | Logs the reason for the loading screen every frame. |
| Force Loading Screen Visible | Off | Always shows the loading screen. |
| Show Loading Screen Additional Secs Even in Editor | On | Applies **Show Loading Screen Additional Secs** in the editor too. |

## Console variables
Four settings have a console variable, so you can change them at runtime. The Project Setting is the starting value.

| Console variable | Setting |
|---|---|
| `CommonLoadingScreen.ShowLoadingScreenAdditionalSecs` | Show Loading Screen Additional Secs |
| `CommonLoadingScreen.ShowSplashScreenAdditionalSecs` | Show Splash Screen Additional Secs |
| `CommonLoadingScreen.LogLoadingScreenReasonEveryFrame` | Log Loading Screen Reason Every Frame |
| `CommonLoadingScreen.AlwaysShow` | Force Loading Screen Visible |

## Command line
| Argument | Description |
|---|---|
| `-NoLoadingScreen` | Never shows the loading screen. Not available in Shipping builds. |

## Upgrading from older versions
Older versions saved the settings under `[/Script/CommonLoadingScreen.CommonLoadingScreenSettings]`. The plugin reads the old section on startup, copies values that are missing from the new section, and logs a warning. Move the values to the new section and remove the old one to get rid of the warning.
