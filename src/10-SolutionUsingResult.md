# Solution for Using the ResultType

```rust
let square = renderer.fill_rect(square_definition);
match square {
    Ok(()) => {}
    Err(error) => println!("{}", error),
}
```
