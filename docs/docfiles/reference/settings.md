---
sidebar_position: 1
description: Every Project Setting and console variable of the CommonLoadingScreen plugin.
---

# Settings and Console Variables

The settings are in **Edit → Project Settings → Plugins → Common Loading Screen**, and are saved to `Config/DefaultGame.ini` under `[/Script/CommonLoadingSettings.CommonLoadingScreenSettings]`.

## Loading Screen
| Setting | Default | Description |
|---|---|---|
| Loading Screen Widget | None | The UMG widget shown as the loading screen. Leave it empty to use the [built-in loading screen](/docfiles/getting_started/built-in-loading-screen). A throbber is shown if the widget can't be loaded. |
| Z Order | `10000` | The Z order of the widget in the viewport. Keep it higher than your other widgets. |
| Automatic Progress | Off | Reports loading progress automatically when a map is loaded. See [Automatic progress](/docfiles/getting_started/progress#automatic-progress). |

### Timing
| Setting | Default | Description |
|---|---|---|
| Additional Hold Time | `2.0` | Seconds to keep the loading screen up after loading has finished, so texture streaming can catch up. |
| Minimum Display Time | `0.0` | The shortest time the loading screen stays up once it is shown, so short loads don't flicker. `0` turns it off. |
| Fade In Duration | `0.0` | Seconds the widget fades in when the loading screen is shown. `0` shows it at once. See [Fading in](/docfiles/concepts/how-it-works#fading-in). |
| Fade Out Duration | `0.0` | Seconds the widget fades out when the loading screen is hidden. `0` removes it at once. See [Fading out](/docfiles/concepts/how-it-works#fading-out). |
| Wait For Key Press | Off | Keeps the loading screen up after a map has loaded until the player presses a key. See [Waiting for a key press](/docfiles/concepts/how-it-works#waiting-for-a-key-press). |

### Status Text
The text to show the player. See [Status text](/docfiles/getting_started/reason#status-text). All texts except the default are empty, and an empty text uses **Default Text**.

| Setting | Default | Description |
|---|---|---|
| Default Text | `Loading...` | The status text when no other text applies. |
| Connecting Text | Empty | Shown while connecting to a server. |
| Loading Map Text | Empty | Shown while a map is loading. |
| Streaming Levels Text | Empty | Shown while streaming levels are loading. |
| Compiling Shaders Text | Empty | Shown while shaders are precompiling. |
| Finishing Text | Empty | Shown during **Additional Hold Time** and **Minimum Display Time**. |
| Key Press Text | `Press any key to continue` | Shown while waiting for a key press. |

## Built-in Loading Screen
Used when **Loading Screen Widget** is empty, and can only be edited then. See [Built-in Loading Screen](/docfiles/getting_started/built-in-loading-screen).

| Setting | Default | Description |
|---|---|---|
| Layout | `Classic` | `Classic`, `Center`, `Letterbox`, `Sidebar` or `Minimal`. |
| Title | Empty | A title, for example the name of the game. |
| Show Tips | On | Shows the tips from **Tips**. |
| Show Progress | On | Shows a progress bar and percentage while something reports progress. |

### Appearance
| Setting | Default | Description |
|---|---|---|
| Spinner | `Ring` | `None`, `Ring`, `Throbber`, `Blocks`, `Bars` or `Image`. |
| Spinner Image | None | The Texture 2D for the `Image` spinner. |
| Logo | None | A logo to show. Not shown with `Minimal`. |
| Logo Size | `128 x 128` | The size of the logo. |
| Theme | `Dark` | `Dark`, `Light`, `Cinematic`, `Midnight` or `Custom`. |
| Background, Panel, Text and Accent Color | Black and white | The colors for the `Custom` theme. |

## Content

### Tips
| Setting | Default | Description |
|---|---|---|
| Tips | Empty | The tips to show. See [Tips](/docfiles/getting_started/tips-slideshow-music#tips). |
| Tip Duration | `6.0` | Seconds each tip is shown. `0` keeps the same tip until the next loading screen. |
| Shuffle Tips | On | Picks the tips in random order instead of the order in the list. |

### Slideshow
| Setting | Default | Description |
|---|---|---|
| Images | Empty | Images to show behind the widget. See [Slideshow](/docfiles/getting_started/tips-slideshow-music#slideshow). |
| Image Duration | `6.0` | Seconds each image is shown. `0` keeps the first image. |
| Crossfade Duration | `1.0` | Seconds the crossfade between two images takes. |
| Shuffle Images | Off | Picks the images in random order instead of the order in the list. |

### Music
| Setting | Default | Description |
|---|---|---|
| Music | None | The sound to play while the loading screen is shown. See [Music](/docfiles/getting_started/tips-slideshow-music#music). |
| Music Volume | `1.0` | The volume of the music. |
| Music Fade In Duration | `1.0` | Seconds the music fades in. |
| Music Fade Out Duration | `1.0` | Seconds the music fades out when the loading screen is hidden. |

### Movies
| Setting | Default | Description |
|---|---|---|
| Movies | Empty | The movies to play while a map loads. See [Adding movies](#adding-movies). |
| Movie Playback Type | `Looped Last Playback` | `Normal Playback` plays the movies once, `Looped Playback` loops all of them and `Looped Last Playback` loops the last one. |
| Movies Are Skippable | Off | The player can skip the movies with a key or mouse click. |
| Wait For Movies To Complete | Off | Plays the movies to the end. When off, they stop as soon as the map has loaded. |
| Show Widget Over Movies | Off | Draws the **Loading Screen Widget** on top of the movies. |
| Use Movie Player During Load Map | Off | Shows the widget with the Movie Player while a map loads, so it keeps animating. See [Keeping the widget animated](/docfiles/concepts/how-it-works#keeping-the-widget-animated-while-a-map-loads). |

### Adding movies
- Put the movie files in `/Content/Movies` in your project, for example `Content/Movies/MyMovie.mp4`.
- Enter only the file name, without the path or extension. For `Content/Movies/MyMovie.mp4` you enter `MyMovie`.
- A movie that can't be found is skipped and a warning is logged.
- Movies are not packaged as assets. Make sure they are copied to the packaged build: turn off **Skip Movies** and add the names to **Movies that are not in UFS** under **Project Settings → Packaging**. With **Use Zen Store** on, the movies end up in the pak file and the Movie Player can't open them.

## Maps
| Setting | Default | Description |
|---|---|---|
| Map Overrides | Empty | Different content for specific maps. See [Map Overrides](#map-overrides). |
| Blocked Map Names | Empty | Maps that never show a loading screen when loaded or travelled to, also with seamless travel, for example `MainMenu`. Use the map's asset name, not the full path. |
| Blocked Maps | Empty | Same as **Blocked Map Names**, but you pick the maps from a list instead of typing their names. Both lists are used. |

### Map Overrides
Use a different widget, movies, tips, images or music while a specific map loads. Add one entry per map.

| Field | Description |
|---|---|
| Map | The map the override is for. |
| Widget | The widget to show while this map loads. Leave it empty to use the default **Loading Screen Widget**. |
| Movies | The movies to play while this map loads. Leave it empty to use the default **Movies**. |
| Tips | The tips to show while this map loads. Leave it empty to use the default **Tips**. |
| Images | The images to show while this map loads. Leave it empty to use the default **Images**. |
| Music | The music to play while this map loads. Leave it empty to use the default **Music**. |

The override is picked when the loading screen is shown, from the map that is being loaded or travelled to. A loading screen that is already up when the load starts keeps its widget and images, but changes to the tips and music of the new map. The first loading screen when the game starts always uses the default widget.

Tips and images [set from Blueprint or C++](/docfiles/getting_started/tips-slideshow-music#changing-tips-and-images-while-the-game-runs) take priority over Map Overrides. Durations, volume, fades and shuffling are shared by all maps. The splash screen always uses the default tips.

The images and music in all entries are loaded when the game starts and stay in memory, so showing the loading screen doesn't hitch.

## Splash Screen
These settings are shown for the matching **Splash Screen Type**, where a type is listed.

| Setting | Type | Default | Description |
|---|---|---|---|
| Disable Splash Screen | | Off | Turns off the splash screen. |
| Splash Screen Type | | `BLACK` | The [splash screen](/docfiles/concepts/splash-screen) on startup: `BLACK`, `LOADING`, `IMAGE` or `VIDEO`. |
| Splash Additional Hold Time | | `2.0` | Seconds to keep the splash screen up after the engine has finished loading. |
| Image | `IMAGE` | Plugin default image | The Texture 2D to show. |
| Stretch | `IMAGE` | `Scale To Fit X` | How the image is scaled. |
| Stretch Direction | `IMAGE` | `Both` | Whether the image may be scaled up, down or both. |
| Loading Text | `LOADING` | `LOADING...` | The text to show. |
| Loading Font | `LOADING` | Regular, size 10 | The font of the text. |

### Overlay
Shown with every type except `VIDEO`. See [Logo, tip and version](/docfiles/concepts/splash-screen#logo-tip-and-version).

| Setting | Default | Description |
|---|---|---|
| Logo | None | The logo at the top of the splash screen. |
| Logo Size | `256 x 256` | The size of the logo. |
| Show Tip | Off | Shows a random tip from **Tips**. |
| Show Version | Off | Shows the Project Version from the project settings. |
| Show Shader Progress | Off | Shows how many shaders are left to precompile. |
| Shader Progress Text | `Compiling shaders: {0}` | The text for the shader progress. `{0}` is the number of shaders left. |

### Splash movies
Shown for the `VIDEO` type.

| Setting | Default | Description |
|---|---|---|
| Movies | Empty | The movies to play on startup. See [Adding movies](#adding-movies). |
| Movie Playback Type | `Normal Playback` | `Normal Playback` plays the movies once, `Looped Playback` loops all of them and `Looped Last Playback` loops the last one. |
| Movies Are Skippable | On | The player can skip the movies with a key or mouse click. |
| Wait For Movies To Complete | On | Plays the movies to the end. When off, they stop as soon as the engine has finished loading. |

## Debugging
| Setting | Default | Description |
|---|---|---|
| Log Reason Every Frame | Off | Logs the reason for the loading screen every frame. |
| Force Visible | Off | Always shows the loading screen. |
| Hold Time Even in Editor | On | Applies **Additional Hold Time** in the editor too. |
| Force Tick Even in Editor | On | Ticks Slate once when the loading screen is shown in the editor, so it is drawn right away. |
| Heartbeat Hang Duration | `0.0` | Seconds the loading screen can be up before the game is considered hung. `0` turns it off. |
| Log Heartbeat Interval | `5.0` | Seconds between each log of what is keeping the loading screen up. `0` turns it off. |

## Console variables
Four settings have a console variable, so you can change them at runtime. The Project Setting is the starting value.

| Console variable | Setting |
|---|---|
| `CommonLoadingScreen.ShowLoadingScreenAdditionalSecs` | Additional Hold Time |
| `CommonLoadingScreen.ShowSplashScreenAdditionalSecs` | Splash Additional Hold Time |
| `CommonLoadingScreen.LogLoadingScreenReasonEveryFrame` | Log Reason Every Frame |
| `CommonLoadingScreen.AlwaysShow` | Force Visible |

## Command line
| Argument | Description |
|---|---|
| `-NoLoadingScreen` | Never shows the loading screen. Not available in Shipping builds. |

## Upgrading from older versions
Older versions saved the settings under `[/Script/CommonLoadingScreen.CommonLoadingScreenSettings]`. The plugin reads the old section on startup and copies values that are missing from the new section. It logs a warning when it copies anything. Move the values to the new section and remove the old one to get rid of the warning. When the new section already has every value, the old section is ignored and only a normal log line says that it can be removed.
