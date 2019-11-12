

Each animation step is displayed in a new frame. We will now draw a rectangle of the size of the canvas, with a different random color.

`sdl` offers methods to draw basic shapes, like rectangles, this needs to be imported. It also offers methods that convert our u8 values into RGB colors, that can be displayed.

```rust
use sdl2::rect::Rect;
use sdl2::pixels::Color;
```rust

pub fn display_rectangle (
    renderer: &mut Canvas<Window>,
    canvas_width: &i32,
    canvas_height: &i32,

) {
    let red: u8 = rand::random();
    let green: u8 = rand::random();
    let blue: u8 = rand::random();

    let drawing_color = Color::RGB(red, green, blue);

    renderer.set_draw_color(drawing_color);
    let square = renderer.fill_rect(Rect::new(0, 0, *canvas_width as u32, *canvas_height as u32));
    match square {
        Ok(()) => {}
        Err(error) => println!("{}", error),
    }
}

//displays the whole grid by repeatedly calling display_cell on every cell
pub fn display_frame(
    renderer: &mut Canvas<Window>,
    canvas_width: &i32,
    canvas_height: &i32,
) {


    renderer.set_draw_color(Color::RGB(0, 0, 0));
    renderer.clear();


    display_rectangle(renderer, canvas_width, canvas_height);


    renderer.present();
}
```
