# Buttons
Buttons are essentially just boxes that return a `boolean` value relating to whether or not it has been pressed.

```csharp
using Hacknet;
using Hacknet.Gui;

using Microsoft.Xna.Framework;

// ...

Button.doButton(int id, int x, int y, int width, int height, string text, Color? color);
```
`Button.doButton` will create a simple button (similar to the rest of the UI) that will return a `bool` value of whether or not it has been clicked. Like every other UI element, this should be put in a `draw` function. An example of how a button might be used is in an executable to exit the executable. For example:
```csharp
using Hacknet;
using Hacknet.Gui;

using Microsoft.Xna.Framework;

// ...

bool exitButton = Button.doButton(183738, bounds.X + 25, bounds.Y + 25, 100, 100, "Exit", Color.Red);

if(exitButton) {
    this.isExiting = true;
    return;
}
```
You can obviously compact this code to make it look nicer as;
```csharp
this.isExiting = Button.doButton(183738, bounds.X + 25, bounds.Y + 25, 100, 100, "Exit", Color.Red);
```
...but the above example works for those still fairly new to C#.

# Unused Buttons
These buttons are largely unused in the modding scene, but you may still find use in them:
```csharp
using Hacknet;
using Hacknet.Gui;

using Microsoft.Xna.Framework;

// ...

Button.doHoldDownButton(int id, int x, int y, int width, int height, string text, bool hasOutline, Color? outlineColor, Color? selectedColor);
```