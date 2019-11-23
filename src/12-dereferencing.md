# Dereferencing

Looking at the function from our game, we can now explain almost all the peculiar signs. One is missing... try running your program without the `*`s.

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

    // let square_definition = Rect::new(0, 0, *canvas_width, *canvas_height);
    let square_definition = Rect::new(0, 0, canvas_width, canvas_height);
    let square = renderer.fill_rect(square_definition);
    match square {
        Ok(()) => {}
        Err(error) => println!("{}", error),

    renderer.present();
}
```

A reference is a type of pointer. You can imagine it as an arrow to a value stored somewhere else.

```rust, editable
let x = 5;
let y = &x;

assert_eq!(5, x);
assert_eq!(5, y);
```

Execute this code.

`x` and `y` don't have the same value. `x` is an integer, and `y` is `&x`, an arrow that points to that integer behind `x`. In order to get to the value `&x` is pointing to, `y` needs to be dereferenced: `*y`.
Change the code above and execute!
