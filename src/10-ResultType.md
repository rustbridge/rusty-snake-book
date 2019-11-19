# Error Handling with the Result Type

1. Check the `sdl2` documentation for the return value of the `fill_rect()` method. Research in the `std` documentation how to use this value.

2. Change the code.





























```rust
let square = renderer.fill_rect(square_definition);
match square {
    Ok(()) => {}
    Err(error) => println!("{}", error),
}
```
