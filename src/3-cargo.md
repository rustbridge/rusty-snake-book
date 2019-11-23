# Cargo and Dependencies

To initialize a new project, run `cargo new`:

```shell
$ cargo new rusty_snake
```

Cargo generated a new new folder called `rusty_snake`. `cd` into the directory to check out what cargo generated.

Open the file `cargo.toml` in the editor of your choice. This is called a manifest, and it contains all of the metadata that Cargo needs to compile your project.

It should look like this:

`cargo.toml`

```rust
[package]
name = "rusty-snake"
version = "0.1.0"
authors = ["Your Name"]
edition = "2018"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]

```

To use SDL2 in rust, we need to add the sdl2 crate as dependency.

Add the following line in the [dependencies] section:
`sdl2 = "0.30.0"`

open `src/main.rs`

Substitute the content of the file with the following code:

```rust
// Dependencies go here




// this function initializes the canvas
fn init(width: u32, height: u32) -> (Canvas<Window>, EventPump) {
    let sdl_context = sdl2::init().unwrap();
    let video_subsystem = sdl_context.video().unwrap();

    let window = video_subsystem
        .window("Game", width + 1, height + 1)
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

// this is main
fn main() {
    println!("Hello, world!");
}
```

Right in the beginning of the File, in the section `// Dependencies go here`, add the following lines:

```rust
use sdl2::video::Window;
use sdl2::pixels::Color;
use sdl2::render::Canvas;
use sdl2::EventPump;
```

In your terminal, go into the folder `/rusty-snake`, and run the command `cargo run`.
What do you see? To get rid of this warning, we need to call `fn init` in `main()`.
