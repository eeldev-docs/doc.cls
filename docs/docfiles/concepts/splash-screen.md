---
sidebar_position: 2
description: The splash screen that the CommonLoadingScreen plugin shows on game startup.
---

# Splash Screen

The splash screen is shown on game startup, before the engine and your loading screen widget are ready. It is drawn with Slate, so it cannot use a UMG widget.

The splash screen is only shown in a packaged or standalone game. It is never shown in the editor or on a dedicated server.

## Splash Screen Type
Choose the type with **Splash Screen Type** in Project Settings.

| Type | What is shown | Settings |
|---|---|---|
| `BLACK` | A black screen | None |
| `LOADING` | A text on a black screen | **Loading Text** and **Loading Font** |
| `IMAGE` | An image | **Image**, **Stretch** and **Stretch Direction** |

With `IMAGE`, the plugin uses its default image if **Image** is not set or is not a Texture 2D.

## Logo, tip and version
These are drawn on top of the `BLACK`, `LOADING` and `IMAGE` types. They are not shown with `VIDEO`.

| Setting | Default | Description |
|---|---|---|
| Splash Screen Logo | None | A Texture 2D shown at the top of the screen. |
| Splash Screen Logo Size | `256 x 256` | The size of the logo. |
| Show Tip On Splash Screen | Off | Shows one random tip from **Tips** at the bottom center. |
| Show Version On Splash Screen | Off | Shows **Project Version** from the project settings in the bottom right corner. |
| Show Shader Progress On Splash Screen | Off | Shows how many shaders are left to precompile in the bottom left corner. Nothing is shown when none are left. |
| Splash Screen Shader Progress Text | `Compiling shaders: {0}` | The text for the shader progress. `{0}` is replaced with the number of shaders left. |

## How long it is shown
The splash screen stays up until the engine has finished loading, and then for **Splash Additional Hold Time** more.

After the splash screen, the normal loading screen takes over while the first map loads.

## Turning it off
Turn on **Disable Splash Screen** in Project Settings.
