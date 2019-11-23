# Adding the snake

Well, maybe not a snake yet, but a square that moves according to your wishes! In this section, you can try to apply what you have learned so far. If you don't know how to continue, you can either ask for help, or look at one way of solving the problems on the next page.

1. In the `lib` folder, make a new file called `snake.rs`.

2. Add the following line to the top of `snake.rs`

   ```rust
   use crate::lib::types::{Cell, SnakeHead, Grid};
   ```

3. Write a function that initialises the snake as a `SnakeHead`. `SnakeHead` is a struct, that contains fields for a row, a column and a `Cell` value. The row and column values need to be `i32` instead of `u32`. Why?

## Defining a tuple

In `fn main()`, after the grid is initialized, we define a tuple for direction. `direction.0` is the row value, `direction.1` is the column value.

```rust
let mut direction = (1, 0);
```

## Movement

1. In `snake.rs`, write a function, that takes a mutable reference of the `SnakeHead`. It calculates a new position with `direction` values and the coordinates from `SnakeHead` and then returns a new `SnakeHead` with an updated position.

2. Write a function, that takes ownership of the grid, changes the color of the square, where the current `SnakeHead` is located. The grid is then the return value.

## Adding User Input

1. Add Events for `up`, `down`, `left` and `right` key.

2. How does the `direction.0` and the `direction.1` value change, when each of these buttons is pushed? Implement it!

## Changing the Game Loop

1. Add this line to the top of `main.rs`:

   ```rust
   use crate::lib::snake;
   ```

2. Call the functions in the following order:

* update position of snake
* update grid with position of snake
* display frame

Run the game! Play the game!
