---
sidebar_position: 6
description: Display the reason for the loading screen in your widget.
---

# Displaying Reason

The reason that you set in **Should Show Loading Screen** can be displayed in your widget to give the player useful feedback.

### Setting up the Widget
- We use a basic widget with a black background and a centered text field to display the reason.

![Widget with a text field](/img/reason-1.png)

### Updating the Reason
- Get the **Loading Screen Manager** and call **Get Debug Reason for Showing or Hiding Loading Screen** to get the reason for showing or hiding the screen.

![Get Debug Reason for Showing or Hiding Loading Screen](/img/reason-2.png)

### The Result
- With the [Actor Example](/docfiles/getting_started/watchers) from the Watchers page, the Loading Screen Manager returns "My Actor wants a loading screen", because we set that as the reason in the Actor.

![The reason in the widget](/img/reason-3.png)

## Custom Text
To show your own text instead, call **Set Loading Screen Custom Text** from anywhere, and read it in the widget with **Get Loading Screen Custom Text**. The plugin never changes the custom text itself.
