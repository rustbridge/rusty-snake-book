# Debugging

## Iterators

One of Rusts features are the error messages that actually help. From the error message we learn, that the type of `events` is called `EventPump`, and where in `sdl2` it is defined. In order to be able to iterate over a type, it has to implement the `Iterator` trait, and apparently, `EventPump` does not. To fix this, we consult the documentation. Besides looking it up on the internet, using the command `cargo doc --open` is an elegant way of getting the documentation for all the crates in your project locally and open in a browser window.

In the `sdl2` crate documentation, go to `EventPump`. Look at the implementation section for this type. Can you find the `Iterator` trait? On the same page, look for a function, that returns an Iterator. On the page of this return type, check, if the `Iterator` trait is implemented.

1. Call the function on events.
2. To make things easier for later, we will give this loop the name `'game`.

It should look like this:

```rust
'game: loop {
    for event in events.poll_iter() {
        // handle user input here
    }
}
```

3. Run the program. From the output on your screen, do you know what to do?

## Mutability
In Rust, variables are immutable by default. You have to make them mutable by declaring them as such with `let mut` instead of just `let`. Iterators need to be mutable, because in each step, an item from the iterator is consumed, to keep track of where it currently is in the iteration sequence. So the internal state of the iterator is changed, which is only be possible, if the variable is declared as mutable.  

4. Run the program. Close the window.
