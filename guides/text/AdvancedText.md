# Creating scaled labels
Since [TextItem](../../docs/gui/TextItem.md) doesn't have a built-in function for creating scaled labels, we'll have to use FNA's built-in `DrawString` function to do so.
```csharp
using Hacknet;
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;

// ...

GuiData.spriteBatch.DrawString(SpriteFont font, string text, Vector2 position, Color color, float rotation, Vector2 origin, float scale, SpriteEffects spriteEffects, float layerDepth);
```
This may look like an intimidatingly long method, but we can rely on constant values for `rotation`, `origin`, `spriteEffects`, and `layerDepth`, like so:
```csharp
GuiData.spriteBatch.DrawString(SpriteFont font, string text, Vector2 position, Color color, 0f, Vector2.Zero, float scale, SpriteEffects.None, 0.01f);
```
So, we only need to worry about `font`, `text`, `position`, `color`, and `scale`. `font` is any `SpriteFont` that Hacknet has in the game, typically under `GuiData`. For example, the default font used in Hacknet can be received as `GuiData.font`. It's also possible to import your own `SpriteFont`s, but this guide will not go over that.

If we want to create a label using the default font that's twice as big as it normally is, we'd need to set scale to `2f`.

> ## [!] C# Tip - Don't Forget Your (f)loat!  
> By default, C# will interpret numbers as either `int` or `double`. Hacknet almost exclusively uses `float`s, so you'll want to use those. You can refer to a number or decimal as a float simply by adding `f` to the end of it. If you're using a variable that is labeled as an `int` or `double` when the method calls for `float`, don't worry - C# will automatically convert the variable to a float.

```csharp
using Hacknet;
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;

// ...

Vector2 pos = new Vector2(0,0);
GuiData.spriteBatch.DrawString(GuiData.font, "This text is twice as big!", pos, Color.White, 0f, Vector2.Zero, 2f, SpriteEffects.None, 0.01f);
```