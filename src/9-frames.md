# Frames.

Each animation step is displayed in a new frame. We will now draw a rectangle of the size of the
window, with a different random color.

`ggez` offers methods to draw basic shapes, like rectangles, in the [`ggez::graphics`] module. It
also offers methods that convert our `u8` values into RGB colors, that can be displayed.

[`ggez::graphics`]: https://docs.rs/ggez/0.5.1/ggez/graphics/index.html

```rust
use ggez::graphics;
use rand;

```

To generate random colors, we'll use the [`rand` crate]. Add it to your `Cargo.toml` as a
dependency. It should now look like this:

```toml
[dependencies]
ggez = "0.5.1"
rand = "0.7"
```

Add the following function to your program.

```rust

fn display_rectangle (
    renderer: &mut Context,
    canvas_width: &f32,
    canvas_height: &f32,
) {
    let red: u8 = rand::random();
    let green: u8 = rand::random();
    let blue: u8 = rand::random();

    let drawing_color = Color::from_rgb(red, green, blue);
    let square_definition = Rect::new(0.0, 0.0, *canvas_width, *canvas_height);
    let mesh = Mesh::new_rectangle(renderer, DrawMode::fill(), rect, drawing_color).unwrap();

    graphics::clear(renderer, Color::from_rgb(0, 0, 0));
    graphics::draw(renderer, &mesh, DrawParam::new()).unwrap();
    graphics::present(renderer).unwrap();
}

```

The function takes the `Context`, as well as the canvas width and height as arguments. It does not
return a value. In the body of the function, the variables red, green and blue are assigned random
`u8` numbers.

Then, the drawing color is defined. We use a function that is provided by `ggez`, the function takes
in three `u8` values and returns a color.

We use [`Rect::new`] to create a new rectangle with its coordinates and dimensions as arguments and
bind it to the variable `square_definition`.

Then we pass both the color and the rectangle to the [`Mesh::new_rectangle`] function, which creates
a `Mesh` that is ready to be drawn to the screen. The [`DrawMode::fill()`] argument ensures that the
rectangle is drawn as a filled shape, not as an outline.

Now that all the objects have been created, let's actually draw them:

* First, [`graphics::clear`] will clear the screen with the given color (in this case, black).
* The [`graphics::draw`] call will then actually do the drawing. It takes an additional
  [`DrawParam`] argument, which would allow us to rotate, scale and otherwise transform the
  drawn mesh. Since we just pass `DrawParam::new()`, the rect will be rendered without
  transformations.
* At the end, [`graphics::present`] will make what we've drawn so far show up in the Window.

Tasks:

1. Do you notice anything peculiar about some of the type declarations in this function?

2. Call this method from the `draw` method in our `EventHandler` impl.

3. Run the program.

[`Rect::new`]: https://docs.rs/ggez/0.5.1/ggez/graphics/struct.Rect.html#method.new
[`Mesh::new_rectangle`]: https://docs.rs/ggez/0.5.1/ggez/graphics/struct.Mesh.html#method.new_rectangle
[`DrawMode::fill()`]: https://docs.rs/ggez/0.5.1/ggez/graphics/enum.DrawMode.html#method.fill
[`DrawParam`]: https://docs.rs/ggez/0.5.1/ggez/graphics/struct.DrawParam.html
[`rand` crate]: https://crates.io/crates/rand
[`graphics::clear`]: https://docs.rs/ggez/0.5.1/ggez/graphics/fn.clear.html
[`graphics::draw`]: https://docs.rs/ggez/0.5.1/ggez/graphics/fn.draw.html
[`graphics::present`]: https://docs.rs/ggez/0.5.1/ggez/graphics/fn.present.html
