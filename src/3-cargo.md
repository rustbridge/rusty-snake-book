# Cargo and Dependencies

To initialize a new project, run `cargo new`:

```shell
$ cargo new rusty_snake
```

Cargo generated a new folder called `rusty_snake`. `cd` into the directory to check out what Cargo generated.

Open the file `Cargo.toml` in the editor of your choice. This is called a manifest, and it contains all of the metadata that Cargo needs to compile your project.

It should look like this:

`Cargo.toml`

```rust
[package]
name = "rusty-snake"
version = "0.1.0"
authors = ["Your Name"]
edition = "2018"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

We will be using the [ggez](https://ggez.rs/) game library, so we'll need to add it as a dependency.

To do that, add the following line in the `[dependencies]` section:

```toml
ggez = "0.5.1"
```

open `src/main.rs`

Substitute the content of the file with the following code:

```rust
// Dependencies go here




// this function initializes the canvas
fn init(width: f32, height: f32) -> (Context, EventsLoop) {
    ContextBuilder::new("Snake", "<your name here>")
        .window_mode(WindowMode::default().dimensions(width, height))
        .build()
        .unwrap()
}

// this is main
fn main() {
    println!("Hello, world!");
}
```

Right in the beginning of the File, in the section `// Dependencies go here`, add the following lines:

```rust
use ggez::{
    conf::WindowMode,
    event::EventsLoop,
    Context, ContextBuilder,
};
```

In your terminal, go into the folder `/rusty-snake`, and run the command `cargo run`.
What do you see? To get rid of this warning, we need to call `fn init` in `main()`.
