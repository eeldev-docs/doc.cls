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
| Splash Screen Type | `BLACK` | The [splash screen](/docfiles/concepts/splash-screen) on startup: `BLACK`, `LOADING` or `IMAGE`. |

## Configuration
| Setting | Default | Description |
|---|---|---|
| Disable Splash Loading Screen | Off | Turns off the splash screen. |
| Force Tick Loading Screen Even in Editor | On | Ticks Slate once when the loading screen is shown in the editor, so it is drawn right away. |
| Show Loading Screen Additional Secs | `2.0` | Seconds to keep the loading screen up after loading has finished, so texture streaming can catch up. |
| Show Splash Screen Additional Secs | `2.0` | Seconds to keep the splash screen up after the engine has finished loading. |
| Loading Screen Heartbeat Hang Duration | `0.0` | Seconds the loading screen can be up before the game is considered hung. `0` turns it off. |
| Log Loading Screen Heartbeat Interval | `5.0` | Seconds between each log of what is keeping the loading screen up. `0` turns it off. |
| Blocked Map Names | Empty | Maps that never show a loading screen when loaded, for example `MainMenu`. Use the map's asset name, not the full path. |

## Splash Screen Configuration
These settings are shown for the matching **Splash Screen Type**.

| Setting | Type | Default | Description |
|---|---|---|---|
| Splash Screen Image | `IMAGE` | Plugin default image | The Texture 2D to show. |
| Splash Screen Stretch | `IMAGE` | `Scale To Fit X` | How the image is scaled. |
| Splash Screen Stretch Direction | `IMAGE` | `Both` | Whether the image may be scaled up, down or both. |
| Splash Screen Loading Text | `LOADING` | `LOADING...` | The text to show. |
| Splash Screen Loading Font | `LOADING` | Regular, size 10 | The font of the text. |

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
