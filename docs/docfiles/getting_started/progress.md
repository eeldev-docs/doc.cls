---
sidebar_position: 8
description: Show how far the loading has come, for example with a progress bar.
---

# Loading Progress

Anything that keeps the loading screen up can report how far it has come, as a value from `0` to `1`. The manager combines the values, and your widget reads the total with **Get Loading Progress** on the Loading Screen Manager.

## Reading the progress in the widget
Call **Get Loading Progress** on the Loading Screen Manager, for example in a binding on a Progress Bar.

- It returns a value from `0` to `1` while something reports progress.
- It returns `-1` when nothing reports progress. Show a throbber instead of a progress bar in that case.
- It never goes backwards while the loading screen is shown, so the bar doesn't jump back when a new task starts.
- It is set to `1` when nothing needs the loading screen anymore, for example during **Show Loading Screen Additional Secs**.
- It is set back to `-1` when the loading screen is hidden.

When several objects report progress, the total is their average.

## Reporting progress from a task
Call **Set Progress** on a [Loading Process Task](/docfiles/getting_started/on-demand) while it works. A task that never calls **Set Progress** is not counted.

```cpp
ULoadingProcessTask* Task = ULoadingProcessTask::CreateLoadingScreenProcessTask(this, TEXT("Loading save game"));
Task->SetProgress(0.5f);
```

## Reporting progress from the interface
Implement **Get Loading Progress** in the Loading Process Interface on the Game State, a Player Controller, one of their components or a [Watcher](/docfiles/getting_started/watchers). Return true and set **Out Progress** to report a value. Return false to not be counted.

```cpp
virtual bool GetLoadingProgress(float& OutProgress) const override
{
	OutProgress = static_cast<float>(NumLoaded) / NumToLoad;
	return true;
}
```

:::info
The progress is updated each frame while the game thread is running. A map that loads with **Open Level** blocks the game thread, so the value stands still during the map load itself. Use the progress for what happens after the map has loaded, for example streaming, data from a server or spawning.
:::
