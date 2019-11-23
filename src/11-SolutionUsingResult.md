# Solution for Using the ResultType

```rust
let square = canvas.fill_rect(square_definition);
match square {
    Ok(()) => {}
    Err(error) => println!("{}", error),
}
```
