---
sidebar_position: 10
description: Use the built-in loading screen with ready-made layouts, spinners and color themes, without creating a widget.
---

# Built-in Loading Screen

The plugin has a ready-made loading screen, so you don't have to create a widget. It is used when **Loading Screen Widget** in Project Settings is empty. Set a widget there, or one in [Map Overrides](/docfiles/reference/settings#map-overrides), to use your own instead.

The settings are under **Built-in Loading Screen** in Project Settings.

## Layouts
| Layout | What is shown |
|---|---|
| `Classic` | Logo and title in the top left corner, with the tip, status, spinner and progress bar along the bottom. |
| `Center` | Everything centered on the screen. |
| `Letterbox` | Logo and title in a band at the top, the rest in a band at the bottom. |
| `Sidebar` | Everything in a panel on the left side. |
| `Minimal` | Only the status and spinner in the bottom right corner. |

## Spinners
| Spinner | Description |
|---|---|
| `None` | No spinner. |
| `Ring` | Dots spinning in a circle. |
| `Throbber` | A row of pulsing pieces. |
| `Blocks` | Bouncing blocks. |
| `Bars` | Bars that grow and shrink. |
| `Image` | Your own Texture 2D, set in **Spinner Image**, rotating. `Ring` is used if the image is not set. |

## Color themes
Choose `Dark`, `Light`, `Cinematic` or `Midnight`. With `Custom` you set the background, panel, text and accent colors yourself.

## Content
- **Title** and **Logo** are optional.
- The **status text** is `Loading...` by default. See [Status Text](/docfiles/getting_started/reason#status-text) for how to show what the game is doing, or your own text.
- **Tips** come from [Tips](/docfiles/getting_started/tips-slideshow-music#tips).
- The **progress bar** and percentage are shown while something reports progress. Turn on [Automatic Progress](/docfiles/getting_started/progress#automatic-progress) to get progress without code.
- A [slideshow](/docfiles/getting_started/tips-slideshow-music#slideshow) replaces the background color.

The logo and spinner image must be included in your packaged build, in the same way as the images for the slideshow.
