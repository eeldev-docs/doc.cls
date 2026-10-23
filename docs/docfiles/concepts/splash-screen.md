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
| `LOADING` | A text on a black screen | **Splash Screen Loading Text** and **Splash Screen Loading Font** |
| `IMAGE` | An image | **Splash Screen Image**, **Splash Screen Stretch** and **Splash Screen Stretch Direction** |

With `IMAGE`, the plugin uses its default image if **Splash Screen Image** is not set or is not a Texture 2D.

## How long it is shown
The splash screen stays up until the engine has finished loading, and then for **Show Splash Screen Additional Secs** more.

After the splash screen, the normal loading screen takes over while the first map loads.

## Turning it off
Turn on **Disable Splash Loading Screen** in Project Settings.
