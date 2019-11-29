# Traits and Event Handlers

When running the program, we shouldn't see anything at this point. If you don't see any error
messages, the program has compiled successfully.

## Traits

We have initialized the canvas, but in order for the program to run continuously, we need a game
loop. Luckily, ggez already provides one for us. To use it, we have to implement its
[`EventHandler`] trait.

[`EventHandler`]: https://docs.rs/ggez/0.5.1/ggez/event/trait.EventHandler.html

Rust's `trait`s are comparable to *interfaces* in Java and C#, or to Swift's *protocols*. They
define a list of methods (or other items) that need to be provided by types implementing the trait.

Traits always need to be implemented for types like `struct`s or `enum`s, so let's start by defining
a `struct Game;` that will later hold all the game state. Now we can implement the trait using the
`impl Trait for Type { ... }` syntax:

```rust
impl EventHandler for Game {
    // ...
}
```

Try compiling the program now. This will initially fail, and the compiler should not just tell you
why, but also how to fix it.

One of the great features of Rust is that compiler errors are often very helpful, so take care to
read the compiler errors. The Rust compiler is here to help you, not make your life harder.

When the trait is imported, the compiler will tell us that we need to implement the `update` and
`draw` methods. Let's add them to the `impl` block:

```rust
fn update(&mut self, ctx: &mut Context) -> Result<(), GameError> {
    Ok(())
}

fn draw(&mut self, ctx: &mut Context) -> Result<(), GameError> {
    Ok(())
}
```

Just like before, `GameError` still needs to be imported via `use`. The compiler will tell us how.

Now that we've implemented the `EventHandler` trait, the next step is to start ggez's game loop at
the end of our `main` function.
