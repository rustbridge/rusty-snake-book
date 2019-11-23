# The Grid

Now that we have set up the very basic framework for graphic output, we want to add some actual game elements.

In the very basic version, the snake will be a square block, moving around in a grid. The food for the snake is a static square block of a different color. As the snake moves and eats the food by moving over it, the snake gets longer by one block. If the snake moves over its own parts, the game is over and restarts. If the snake moves out of the canvas, it reenters it on the other side.

## Structs and Vectors

Structs are a datatype, that can contain several fields, the fields do not have to be of the same datatype.
Using structs, we will define our own data types for the grid and the cells. Both struct definition go into `types.rs`

1. Let's define the `Grid`-struct. It has one field named `grid`. The datatypes are vectors of `Cell`s inside a vector. The items in the inner vector are rows, the items in the outer vector colums.

   ``` rust
   pub struct Grid {
       pub grid: Vec<Vec<Cell>>,
   }
   ```

2. Write your own struct for the `Cell` type. This datatype is used to define the color of a cell, so it needs fields for each RGB-value. The data type of the RGB-values is an unsigned 8-bit integer: `u8`.

3. Add the following lines to `mod.rs` to be able to use the types there.

   ```rust
   pub mod types;

   use types::{Grid, Cell};
   ```

   Next, we need to initialize the grid.

4. Add this function to `mod.rs`

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

5. Discuss in your group, what this function does, line by line.

6. Add the following line in `fn main()` before you spawn the thread.

   ```rust
   let mut grid = lib::grid_init(columns, rows);
   ```
