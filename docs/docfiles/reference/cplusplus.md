---
sidebar_position: 3
sidebar_label: C++ API
description: Use the CommonLoadingScreen plugin from C++.
---

# C++ API

Add the module to your `.Build.cs`:

```csharp
PrivateDependencyModuleNames.AddRange(new string[] { "CommonLoadingScreen" });
```

## Keep the loading screen up from an Actor or Component
Implement `ILoadingProcessInterface` and override `ShouldShowLoadingScreen`. This works on the Game State, a Player Controller and their components without any registration.

```cpp
#include "LoadingProcessInterface.h"

UCLASS()
class AMyGameState : public AGameStateBase, public ILoadingProcessInterface
{
	GENERATED_BODY()

public:
	virtual bool ShouldShowLoadingScreen(FString& OutReason) const override
	{
		if (!bWorldReady)
		{
			OutReason = TEXT("Waiting for the world to be ready");
			return true;
		}
		return false;
	}

private:
	bool bWorldReady = false;
};
```

:::warning
Always set `OutReason` when you return true. An empty reason triggers an `ensure`.
:::

Any other object must be registered with the manager:

```cpp
#include "LoadingScreenManager.h"

if (ULoadingScreenManager* Manager = ULoadingScreenManager::Get(this))
{
	Manager->RegisterLoadingProcessor(this);
}
```

Call `UnregisterLoadingProcessor(this)` when it is done. The manager holds the object weakly, so a destroyed object is skipped automatically.

## Show the loading screen on demand
```cpp
#include "LoadingProcessTask.h"

ULoadingProcessTask* Task = ULoadingProcessTask::CreateLoadingScreenProcessTask(this, TEXT("Saving the game"));

// later
Task->Unregister();
```

The manager keeps the task alive until `Unregister` is called.

Pass a timeout, or tie the task to the context object, to make sure it can't keep the loading screen up forever:

```cpp
ULoadingProcessTask* Task = ULoadingProcessTask::CreateLoadingScreenProcessTask(this, TEXT("Saving the game"), 30.0f, true);
```

| Parameter | Default | Description |
|---|---|---|
| `TimeoutSeconds` | `0.0f` | The task is unregistered after this many seconds. `0` means no timeout. |
| `bUnregisterWithContextObject` | `false` | The task is unregistered when the world context object is destroyed. |

An expired task is unregistered by the manager and a warning is logged. Check it with `Task->IsExpired()`.

## Report loading progress
Call `Task->SetProgress(0.5f)` on a task, or override `GetLoadingProgress` in `ILoadingProcessInterface`. Read the total with `ULoadingScreenManager::GetLoadingProgress()`, or bind `OnLoadingProgressChanged` to be told when it changes. See [Loading Progress](/docfiles/getting_started/progress).

```cpp
virtual bool GetLoadingProgress(float& OutProgress) const override
{
	OutProgress = static_cast<float>(NumLoaded) / NumToLoad;
	return true;
}
```

## React to the loading screen
```cpp
if (ULoadingScreenManager* Manager = ULoadingScreenManager::Get(this))
{
	Manager->OnLoadingScreenVisibilityChangedDelegate().AddUObject(this, &ThisClass::HandleLoadingScreenVisibilityChanged);
}

void AMyActor::HandleLoadingScreenVisibilityChanged(bool bIsVisible)
{
}
```

## ULoadingScreenManager
| Function | Description |
|---|---|
| `static ULoadingScreenManager* Get(UObject* WorldContextObject)` | Returns the manager, or `nullptr` on a dedicated server. |
| `void RegisterLoadingProcessor(TScriptInterface<ILoadingProcessInterface>)` | Registers an object that is asked whether the loading screen should be shown. |
| `void UnregisterLoadingProcessor(TScriptInterface<ILoadingProcessInterface>)` | Unregisters it. |
| `void AddLoadingScreenWatcher(UObject*)` | Adds a [Watcher](/docfiles/getting_started/watchers). |
| `void RemoveLoadingScreenWatcher(UObject*)` | Removes a Watcher. |
| `void SetCustomLoadingScreenText(FString)` | Sets the custom text. |
| `void SetCustomLoadingScreenDisplayText(const FText&)` | Sets the custom text as a localizable text. |
| `bool GetLoadingScreenDisplayStatus() const` | True while the loading screen is shown. |
| `float GetLoadingProgress() const` | How far the loading has come, from `0` to `1`, or `-1` if nothing reports progress. |
| `FString GetDebugReasonForShowingOrHidingLoadingScreen() const` | The current reason. |
| `FString GetLoadingScreenCustomText() const` | The custom text as a string. |
| `FText GetLoadingScreenCustomDisplayText() const` | The custom text as a localizable text. |
| `FString GetCurrentLoadingMap() const` | The map that is loading, or was loaded last. |
| `bool IsLoadingScreenFadingOut() const` | True while the widget fades out after the loading screen was hidden. |
| `FOnLoadingScreenVisibilityChangedDelegate& OnLoadingScreenVisibilityChangedDelegate()` | Native delegate for visibility changes. |
| `FText GetCurrentLoadingScreenTip() const` | The tip to show. |
| `FOnLoadingScreenTipChanged OnLoadingScreenTipChanged` | Dynamic delegate that is broadcast when a new tip is selected. |
| `FText GetLoadingScreenStatusText() const` | The text to show the player. |
| `FOnLoadingScreenStatusTextChanged OnLoadingScreenStatusTextChanged` | Dynamic delegate that is broadcast when the status text changes. |
| `void SetLoadingScreenTips(const TArray<FText>&)` | Replaces the tips while the game runs. |
| `void ClearLoadingScreenTips()` | Goes back to the tips from the settings. |
| `void SetLoadingScreenImages(const TArray<UTexture2D*>&)` | Replaces the images from the next loading screen. |
| `void ClearLoadingScreenImages()` | Goes back to the images from the settings. |
| `bool IsWaitingForKeyPress() const` | True while the loading screen waits for a key press. |
| `void ContinueFromLoadingScreen()` | Stops waiting for a key press. |
| `FOnWaitingForKeyPressChanged OnWaitingForKeyPressChanged` | Dynamic delegate that is broadcast when the wait starts and stops. |
| `FOnLoadingProgressChanged OnLoadingProgressChanged` | Dynamic delegate that is broadcast when the progress changes. |

## ULoadingProcessTask
| Function | Description |
|---|---|
| `static ULoadingProcessTask* CreateLoadingScreenProcessTask(UObject* WorldContextObject, const FString& Reason, float TimeoutSeconds = 0.0f, bool bUnregisterWithContextObject = false)` | Creates and registers a task. |
| `void Unregister()` | Unregisters the task. |
| `void SetShowLoadingScreenReason(const FString&)` | Changes the reason. |
| `FString GetShowLoadingScreenReason() const` | The reason. |
| `void SetProgress(float)` | Reports progress from `0` to `1`. |
| `void SetStatusText(const FText&)` | Sets a text to show the player. |
| `bool IsExpired() const` | True when the task has timed out, or its context object is gone. |

## Log category
All modules of the plugin log to `LogLoadingScreen`. It is exported from the `CommonLoadingSettings` module, so you can use it in your own code by including `CommonLoadingScreenLog.h` and adding `CommonLoadingSettings` to your dependencies.
