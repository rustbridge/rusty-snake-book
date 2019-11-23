# Handling User Input

## enums and match

Yeah, it's kind of hard to close the window. The reason for this is, that we have not told our program how to deal with events, so it continues to run and we have to force it to quit. That's uncomfortable, let's change that.

Go to the `sdl2` documentation. Go to the `event` module, find the `Event` `enum`. An `enum` in Rust is a type that represents data that is one of several possible variants. Each variant in the `enum` can optionally have data associated with it. Look at the possible `event` variants in the declaration of `Event`. We want to end the program by pushing `esc`. What variant are we looking for?

In our game loop, we iterate over `events`. Depending on what kind of `event` is happening, we want the program to react in different ways. Pushing `space` means something different, then pushing `esc`. We will `match` the `event` to the variants of the enum `Event`. `match` is a way to control the the flow of the program, when there are several possible options, similar to `if` `else` statements.

1. To be able to use the enum and work with keyboard input, we need to add the following dependencies:

```rust
use sdl2::event::Event;
use sdl2::keyboard::Keycode;
```

2. Enter the following lines into the `for` loop. `match` compares the value of the `event`-variable to the variants of the enum `Event`. If the value of the `event`-variable is a pressed `esc`-key, the `'game`-loop breaks. If value is something else, the loop continues. The last part of a `match` always needs to be `_ =>`, the case that covers all cases that are not explicitly defined.

```rust
match event {
    Event::KeyDown {
        keycode: Some(Keycode::Escape),
        ..
    } => break 'game,
    _ => continue 'game,
}
```

3. Run the program, try if the user input you implemented works!
4. To be able to close the window with a mouse click, change the first line of the `match` to include `Event::Quit { .. }`. The `'game` -loop breaks now if either the `esc`-key is pressed, or the quit-button is clicked with the curser.

```rust
match event {
    Event::Quit {
        ..
    } | Event::KeyDown {
        keycode: Some(Keycode::Escape),
        ..
    } => break 'game,
    _ => continue 'game,
}
```
