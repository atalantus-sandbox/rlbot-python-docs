---
description: Render extra UI elements on the game screen
---

# Rendering

An incredibly useful new addition to RLBot v4 is the rendering feature. It allows you to draw objects on screen, which can make debugging and testing your bot so much easier.

The renderer object is built into the BaseAgent class, so you don't need to import anything other than the BaseAgent. Each time you want to render something, you start with `self.renderer.begin_rendering()` and end with `self.renderer.end_rendering()`. The rendering code goes in between the `begin_rendering()` and `end_rendering()`. Let's take a look at an example:

```python
class RenderingTutorial(BaseAgent):
    def get_output(self, packet: GameTickPacket) -> SimpleControllerState:
        controller = SimpleControllerState()

        self.renderer.begin_rendering()
        self.renderer.draw_rect_2d(20, 20, 200, 200, True, self.renderer.black())
        self.renderer.end_rendering()

        return controller
```

We can see here that every `get_output` call, the on-screen drawings get updated. In this example, the `draw_rect_2d` method is used. Let's go over all the methods you can use:

\(Note: The argument names aren't exactly what appear in the framework itself, but the argument positions are the same\)

The rendering feature in RLBot is a great new addition, and it should definitely help you with making your bot. For example, you could draw the predicted ball path, or draw where the bot wants to go. Have fun with it and see what you can do!

## Methods

### create\_color

`create_color(a, r, g, b)`

This doesn't draw anything on screen, but it is used for creating colors that you can use for the other methods that draw on screen.

* **a, r, g, b** - Alpha, red, green, blue. From 0 to 255.

### draw\_rect\_2d {#wiki_renderer.draw_rect_2d}

`draw_rect_2d(x, y, width, height, fill, color)`

This draws a rectangle on screen.

* **x, y** - The top left x and y screen coordinates for the rectangle. \(0, 0\) is the top left of the screen.
* **width, height** - The width and height of the rectangle.
* **fill** - If True, the entire rectangle is filled with _color_, else it is just an outline of _color_.
* **color** - The color of the rectangle. Can be `renderer.black()`, `renderer.white()`, or `renderer.create_color(a, r, g, b)`.



