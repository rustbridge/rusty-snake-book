# Frames.

Each animation step is displayed in a new frame. We will now draw a rectangle of the size of the canvas, with a different random color.

`sdl` offers methods to draw basic shapes, like rectangles, this needs to be imported. It also offers methods that convert our u8 values into RGB colors, that can be displayed.

```rust
use sdl2::rect::Rect;
use rand;

```

`rand` is another library we are using. To activate it, add it to your `Cargo.toml` as a dependency. It should now look like this:

```
[dependencies]
sdl2 = "0.30.0"
rand = "0.7"
```

Add the following function to your program.

```rust

fn display_rectangle (
    renderer: &mut Canvas<Window>,
    canvas_width: &u32,
    canvas_height: &u32,

) {
    let red: u8 = rand::random();
    let green: u8 = rand::random();
    let blue: u8 = rand::random();

    renderer.clear();

    let drawing_color = Color::RGB(red, green, blue);
    renderer.set_draw_color(drawing_color);

    let square_definition = Rect::new(0, 0, *canvas_width, *canvas_height);
    renderer.fill_rect(square_definition);

    renderer.present();
}

```

The function takes the canvas, as well as the canvas width and height as arguments. It does not return a value. In the body of the function, the variables red, green and blue are assigned random `u8` numbers.
The `clear()` method is called on the renderer, this clears the canvas. When, like in our case, the entire canvas is drawn over, this does not really matter, but it's a good habit, to think of this.
Then, the drawing color is defined. We use a function that is provided by `sdl2`, the function takes in three `u8` values and returns a color.
The method `set_draw_color()` is called on the renderer, with `drawing_color` as argument.

We create a new rectangle with it's minimum and maximum x and y values as arguments and bind it to the variable `square_definition`. This variable is then passed to the method `fill_rect()`. Our square is rendered and put into the back buffer.

The last line updates the screen with all the rendering done since the last update.

Do you notice anything peculiar about some of the type declarations in this function?

Try calling this function for every `'game` loop iteration in your main program.

Run the program.
