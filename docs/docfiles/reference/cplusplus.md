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
| `bool GetLoadingScreenDisplayStatus() const` | True while the loading screen is shown. |
| `FString GetDebugReasonForShowingOrHidingLoadingScreen() const` | The current reason. |
| `FString GetLoadingScreenCustomText() const` | The custom text. |
| `FString GetCurrentLoadingMap() const` | The map that is loading, or was loaded last. |
| `FOnLoadingScreenVisibilityChangedDelegate& OnLoadingScreenVisibilityChangedDelegate()` | Native delegate for visibility changes. |
