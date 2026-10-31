---
sidebar_position: 5
description: What changed in each version of the CommonLoadingScreen plugin.
---

# Changelog

## 1.2.0
### New
- **Loading Screen Fade Out Duration**: the widget fades out when the loading screen is hidden. See [Fading out](/docfiles/concepts/how-it-works#fading-out).
- **Minimum Loading Screen Display Time**: the loading screen stays up for at least this long once shown.
- **Map Overrides**: a different widget or different movies per map. See [Map Overrides](/docfiles/reference/settings#map-overrides).
- **Blocked Maps**: pick blocked maps from a list. **Blocked Map Names** still works.
- **Create Loading Screen Process Task** has the advanced pins **Timeout Seconds** and **Unregister With Context Object**, so a task can stop by itself. See [Show on Demand](/docfiles/getting_started/on-demand#making-the-task-stop-by-itself).
- New task nodes **Is Expired** and **Get Show Loading Screen Reason**.
- **On Loading Progress Changed** event on the Loading Screen Manager.
- **Set Loading Screen Custom Display Text** and **Get Loading Screen Custom Display Text** for localizable text.
- **Is Loading Screen Fading Out** on the Loading Screen Manager.

### Fixed
- Loading screen movies were played when loading a blocked map.
- The extra hold time could apply when travelling to a blocked map.
- The warning about the legacy config section was logged on every startup, also when nothing was migrated.
- Some messages were logged to `LogTemp` instead of `LogLoadingScreen`.

### Changed
- The default loading screen widget is loaded when the game starts, so the first loading screen doesn't hitch.
- `LogLoadingScreen` is now exported from the `CommonLoadingSettings` module.
