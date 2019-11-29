# References and Mutability

In the last chapter, we've implemented the `EventHandler` trait for our `Game` struct. Now we'd like
to start ggez's game loop. To do that, we need to call the function [`ggez::event::run`][`run`] and
pass the right arguments.

The [`run`] function expects its arguments to be passed *by reference*. A reference allows a
function to access variables defined in the calling function (or somewhere else entirely), without
having to copy or move them around. You can create references to values by prefixing the value with
`&`. For example:

```rust
let x = 0u32;
let reference = &x;  // `reference` has type `&u32`
```

The function we want to call expects *mutable* references (a reference that can be used to modify
the original object), which are created with `&mut var`.

Try calling the [`run`] function, passing `&mut` references as parameters. What happens?

> In Rust, variables are immutable by default. You have to make them mutable by declaring them as
> such. This is done by putting the `mut` keyword in front of the variable's name (eg. `let mut x`).

[`run`]: https://docs.rs/ggez/0.5.1/ggez/event/fn.run.html
