# Initializing the Canvas

Our game needs a canvas, where all the games graphic is rendered. Let's initialize it.

## Functions and variables


Let's take a closer look at `fn init`.

`main.rs`

```rust
// this function initializes the canvas
fn init(width: f32, height: f32) -> (Context, EventsLoop) {
    ContextBuilder::new("Snake", "<your name here>")
        .window_mode(WindowMode::default().dimensions(width, height))
        .build()
        .unwrap()
}
```

 `fn` declares the function, `init` is its name. The function takes two parameters, `width` and `height`. Rust is a type safe language, so the types of the parameters need to be explicitly indicated. In this example, the type of both parameters is `f32`, a 32-bit floating-point number. The return types also need to be specifically named. `fn init` returns two values in a bracket, separated by a comma. The types of these values are defined in the `ggez`-crate. We'll ignore the body of the function for now.

1. In `main()`, delete the `println!` statement.

2. Declare the variables `canvas_width` and `canvas_height`, each with the value `500.0`.

3. Call the function by adding the following line:

   ```rust
   let (context, events) = init(canvas_width, canvas_height);
   ```

4. In the terminal enter `cargo run`. What happens?
