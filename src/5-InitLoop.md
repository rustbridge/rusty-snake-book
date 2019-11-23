# The Game Loop

## Loops

When running the program, we shouldn't see anything. If you don't see any error messages, the program compiles.
We have initialized the canvas, but in order for the program to run continuously, we need a game loop (aka event loop).

> 💡 Unlike a command-line program, which performs a single pre-specified task and once done terminates, a program with a GUI (such as a game) is commonly expected to stay open until the user decides to close the program (e.g. by clicking on "Quit" in the main menu). For this to work one commonly makes use of an infinite loop (here: `loop { … }`), within which on each iteration one asks an event source for any events that have occurred since the last iteration and passes them to the program for handling. Over and over again.

1. After the last line inside `fn main()` add a

    ```rust
    loop {
        
    }
    ```

2. Inside this `loop`, iterate over `event` in `events.poll_iter()` with a `for` loop.
3. Run the program. In your group, read and discuss the output on the screen. What information does it provide?
