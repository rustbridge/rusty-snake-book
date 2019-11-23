# Modularization

## Creating Modules

Since this project will be bigger then  a couple of lines of code, things will be more organised if we split it up into modules. To do this, make a new folder in inside the `src` folder, and call it `lib`. Inside `lib`, create `mod.rs` and `types.rs`.

```plain
.
├── rusty snake
│    ├── src
│    │    ├── lib
│    │    │    ├── mod.rs
│    │    │    └── types.rs
│    │    │
│    │    └──  main.rs
│    │
│    ├── Cargo.lock
│    └── Cargo.toml
└── ...
```

Move all functions you wrote to `mod.rs`. In order for this to work, all dependencies, these functions need, also need to be declared in `mod.rs`. If they are not used in `main.rs`, you can delete them there.

## Dependencies

Dependencies for the moved functions have to be moved to `mod.rs` too.

## Making Functions and structs Public

In order for a function to be accessible in `main.rs`, it needs to be marked with `pub`.

## Accessing the Modules in `main.rs`

Before `fn main()` add the following line:

```rust
pub mod lib;
```

Functions now have to be called in the namespace of the module:

```rust
let (canvas, mut events) = lib::init(canvas_width, canvas_height);
```
