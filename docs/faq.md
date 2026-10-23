---
sidebar_position: 4
sidebar_label: FAQ & Troubleshooting
description: Answers to common questions and problems with the CommonLoadingScreen plugin.
---

# FAQ & Troubleshooting

## The loading screen never goes away
Something is still asking for it. Turn on **Log Loading Screen Reason Every Frame** in Project Settings, or run `CommonLoadingScreen.LogLoadingScreenReasonEveryFrame 1` in the console, and the log shows the reason every frame. You can also show the reason in your widget, see [Displaying Reason](/docfiles/getting_started/reason).

Common causes:
- A **Should Show Loading Screen** function that still returns true.
- A task from **Create Loading Screen Process Task** that was never unregistered. The task keeps the loading screen up until you call **Unregister** on it.
- **Force Loading Screen Visible** is on in Project Settings.
- No local Player Controller exists yet. The loading screen stays up until at least one does, or until all of them do in split screen.

## I only see a spinning throbber instead of my widget
The plugin could not load the **Loading Screen Widget** set in Project Settings, and falls back to a throbber. Check that the widget is set and that it is included in your packaged build. The log shows `Failed to load the loading screen widget`.

## The loading screen behaves differently in the editor
The loading screen works in PIE, with a few differences:
- The extra hold time only applies when **Show Loading Screen Additional Secs Even in Editor** is on. It is on by default.
- Input is not blocked while the loading screen is shown.
- The splash screen is never shown. Test it in a packaged or standalone game.

## The splash screen does not show
- Check that **Disable Splash Loading Screen** is off.
- The splash screen is only shown in a packaged or standalone game, never in the editor.
- With the **IMAGE** type, check that the image is a Texture 2D. The plugin's default image is used if none is set.

## The loading screen shows on my main menu
Add the map name to **Blocked Map Names** in Project Settings. Use the map's asset name, for example `MainMenu`, not the full path.

## Can I skip the loading screen while testing?
Start the game with `-NoLoadingScreen` on the command line. This works in all builds except Shipping.

## Does the loading screen work on a dedicated server?
No loading screen is created on a dedicated server. Listen servers and clients show it as normal.
