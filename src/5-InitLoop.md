# The Game Loop

## Loops

When running the program, we shouldn't see anything. If you don't see any error messages, the program compiles.
We have initialized the canvas, but in order for the program to run continuously, we need a game loop.

1. After the last line inside `fn main()` add a `loop {}`.

2. Inside this `loop`, iterate over `event` in `events.poll_iter()` with a `for` loop.

3. Run the program. In your group, read and discuss the output on the screen. What information does it provide?
