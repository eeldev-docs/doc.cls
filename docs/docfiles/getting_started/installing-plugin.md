---
sidebar_position: 1
description: How to install the CommonLoadingScreen plugin and move it to your project.
---

# Installing the plugin

The plugin is installed from the Epic Games Launcher.

## Locate the plugin
- Add the plugin to your library on [Fab](https://www.fab.com/listings/356807ad-0cb8-40a4-917a-fcf938637afb).
- In the Epic Games Launcher, open **Unreal Engine → Library → Fab Library** and search for **Common Loading Screen**.

![Locate the plugin](/img/installing-1.png)

## Select Engine Version
- Click **Install to Engine** and select the engine version to install it to.

![Select engine version](/img/installing-2.png)

## Verify plugin installation
- Verify that the plugin was installed.

![Plugin installed](/img/installing-3.png)
![Plugin enabled](/img/installing-4.png)

## Move the Plugin (Optional)
This step is optional, but we recommend moving installed plugins to your project's `Plugins` folder.

### Locate the plugin install location
- Locate the plugin. A common install location is:

```
C:\Program Files\Epic Games\UE_5.x\Engine\Plugins\Marketplace
```

![Plugin install location](/img/move-1.png)

### New location
- Move the `CommonLoadingScreen` folder to your project's `Plugins` folder. Create the `Plugins` folder if it doesn't exist.

![Project Plugins folder](/img/move-2.png)

## Using the plugin from C++
If you call the plugin from C++, add the `CommonLoadingScreen` module to your module's `.Build.cs`:

```csharp
PrivateDependencyModuleNames.AddRange(new string[] { "CommonLoadingScreen" });
```

See [C++ API](/docfiles/reference/cplusplus) for examples.

## Next step
[Configure the plugin](/docfiles/getting_started/configuring-plugin).
