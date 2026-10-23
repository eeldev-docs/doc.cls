---
sidebar_position: 5
description: Show the loading screen on demand from any Blueprint with a world context.
---

# Show on Demand

You can show the loading screen on demand from any Blueprint that has a world context, without implementing any interface.

Call **Create Loading Screen Process Task** with a reason. The loading screen is shown until you call **Unregister** on the returned task.

## Player Controller Example
- This example shows the loading screen for 4 seconds, called from the Player Controller Blueprint.

![Create Loading Screen Process Task](/img/on-demand.png)

:::warning
The plugin keeps the task alive until you call **Unregister** on it. If you never call **Unregister**, the loading screen stays up.
:::

## Updating Reason
- You can update the loading screen reason at any time with **Set Show Loading Screen Reason** on the task.

![Set Show Loading Screen Reason](/img/on-demand-reason.png)

## The Result
![The loading screen in PIE](/img/on-demand-1.png)

![The result](/img/on-demand-2.png)
