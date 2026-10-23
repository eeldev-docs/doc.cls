---
sidebar_position: 2
description: The Project Settings of the CommonLoadingScreen plugin.
---

# Configuring the Plugin

You configure the plugin in **Edit → Project Settings → Plugins → Common Loading Screen**. Every setting is described in detail in [Settings and Console Variables](/docfiles/reference/settings).

## Project Settings
![Project Settings](/img/project-settings.png)

### Display
- **Loading Screen Widget**

  The widget that is displayed when switching maps, or when something tells the plugin to display the loading screen.

- **Loading Screen ZOrder**

  This number should be higher than your other widgets, so the loading screen stays on top of them.

- **Splash Screen Type**

  The splash screen shown on game startup: `BLACK`, `LOADING` or `IMAGE`. See [Splash Screen](/docfiles/concepts/splash-screen).

### Configuration
- **Disable Splash Loading Screen**

  Turns off the splash screen on game startup.

- **Force Tick Loading Screen Even in Editor**

  Lets the loading screen tick also when running in the editor.

- **Show Loading Screen Additional Secs**

  Even after the loading screen has "finished", it continues to display for this many seconds.

- **Show Splash Screen Additional Secs**

  The splash screen is displayed for this many extra seconds on game startup.

- **Loading Screen Heartbeat Hang Duration**

  Detects if the loading screen has hung or frozen.

- **Log Loading Screen Heartbeat Interval**

  How often to log what is keeping the loading screen up.

- **Blocked Map Names**

  Maps that never show a loading screen when they are loaded.

### Debugging
- **Log Loading Screen Reason Every Frame**

  Logs the reason why the loading screen is currently shown.

- **Force Loading Screen Visible**

  Forces the loading screen to always show.

- **Show Loading Screen Additional Secs Even in Editor**

  Shows the loading screen for the additional seconds also when running in the editor.

## Next step
[Create your loading screen widget](/docfiles/getting_started/using-plugin).
