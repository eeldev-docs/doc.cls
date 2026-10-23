---
sidebar_position: 7
description: Turn on verbose logging for the CommonLoadingScreen plugin.
---

# Additional Logging

Turn on debugging output to get more information on what the plugin is doing. Add these lines to your `DefaultEngine.ini`:

## DefaultEngine.ini
```ini
[Core.Log]
LogLoadingScreen=Verbose
```

Use `VeryVerbose` to also log every check the plugin makes each frame.

You can also change the level at runtime with the console command `Log LogLoadingScreen Verbose`.

## Log the reason every frame
To see what keeps the loading screen up, turn on **Log Loading Screen Reason Every Frame** in Project Settings, or run this in the console:

```
CommonLoadingScreen.LogLoadingScreenReasonEveryFrame 1
```

## Finding Logs
Logs are saved in your `Project\Saved\Logs` folder.
