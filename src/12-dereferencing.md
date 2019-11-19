# Dereferencing

Looking at the function from our game, we can now explain almost all the peculiar signs. One is missing.... try running the program without the `*`s.

[Explain what dereferncing means]

```rust

fn display_frame (
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
    let square = renderer.fill_rect(square_definition);
    match square {
        Ok(()) => {}
        Err(error) => println!("{}", error),

    renderer.present();
}

```
