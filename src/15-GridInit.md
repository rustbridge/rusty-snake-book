# The Grid

Now that we have set up the very basic framework for graphic output, we want to add some actual game elements.

In the very basic version, the snake will be a square block, moving around in a grid. The food for the snake is a static square block of a different color. As the snake moves and eats the food by moving over it, the snake gets longer by one block. If the snake moves over its own parts, the game is over and restarts. If the snake moves out of the canvas, it reenters it on the other side.


### Structs and Vectors

Using structs, we will define our own data types for the grid and the cells. [Explain structs].

1. The `Grid`-struct has one field named `grid`. The datatypes are vectors of `Cell`s inside a vector. The items in the inner vector are rows, the items in the outer vector colums.

``` rust
pub struct Grid {
    pub grid: Vec<Vec<Cell>>,
}
```
2. Write your own struct for the `Cell` type. This datatype is used to define the color of a cell, so it needs fields for each RGB-value. The data type of the RGB-values is an unsigned 8-bit integer: `u8`.

Next, we need to initialize the grid.

3. Add this function to `mod.rs`

```rust
pub fn grid_init(nx_cells: u32, ny_cells: u32) -> Grid {
    let mut grid_vector = Vec::new();

    for row in 0..ny_cells {
        grid_vector.push(Vec::new());
        for _column in 0..nx_cells {
            grid_vector[row as usize].push(Cell {
                red: 35_u8,
                green: 15_u8,
                blue: 13_u8,
            });
        }
    }
    let grid = Grid { grid: grid_vector };

    grid
}
```
4. Discuss in your group, what this function does, line by line.
5. Add the following line before you spawn the thread.

```rust
let mut grid = lib::grid_init(columns, rows);
```
