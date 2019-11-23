# Initializing the Canvas

Our game needs a canvas, where all the games graphic is rendered. Let's initialize it.

## Functions and variables


Let's take a closer look at `fn init`.

`main.rs`

```rust

// this function initializes the canvas
fn init(width: u32, height: u32) -> (Canvas<Window>, EventPump) {
    let sdl_context = sdl2::init().unwrap();
    let video_subsystem = sdl_context.video().unwrap();

    let window = video_subsystem
        .window("Rusty Snake", width as u32 + 1, height as u32 + 1)
        .position_centered()
        .build()
        .unwrap();

    let mut canvas = window.into_canvas().present_vsync().build().unwrap();

    canvas.set_draw_color(Color::RGB(0, 0, 0));
    canvas.clear();
    canvas.present();

    let event_pump = sdl_context.event_pump().unwrap();
    (canvas, event_pump)
}

```
 `fn` declares the function, `init` is its name. The function takes two parameters, x and y. Rust is a type safe language, so the types of the parameters need to be explicitly indicated. In this example, the type of both parameters is `u32`, a 32bit unsigned integer. The return types also need to be specifically named. `fn init` returns two values in a bracket, separated by a comma. The types of these values are defined in the `sdl2`-crate. We'll ignore the body of the function for now.

1. In `main()`, delete the `println!` statement.

2. Declare the variables `canvas_width` and `canvas_height`, each with the value `720_u32`. `_u32` makes this number explicitly an unsigned 32bit integer.

3. Call the function by adding the following line:

   ```rust
   let (canvas, events) = init(canvas_width, canvas_height);
   ```

4. In the terminal enter `cargo run`. What happens?
