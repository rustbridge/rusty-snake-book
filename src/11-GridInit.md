# The Grid

Now that we have set up the very basic framework for graphic output, we want to add some actual game elements.

In the very basic version, the snake will be a square block, moving around in a grid. The food for the snake is a static square block of a different color. As the snake moves and eats the food by moving over it, the snake gets longer by one block. If the snake moves over its own parts, the game is over and restarts. If the snake moves out of the canvas, it reenters it on the other side.


### structs and vectors

Using structs, we will define our own data types for the grid and the cells. [Explain structs].

1. The `Grid`-struct has one field named `grid`. The datatypes are vectors of `Cell`s inside a vector. The items in the inner vector are rows, the items in the outer vector colums.

``` rust
struct Grid {
    grid: Vec<Vec<Cell>>,
}
```
2. Write your own struct for the Cell type. This datatype is used to define the color of a cell, so it needs fields for each RGB-value. The data type of the RGB-values is an unsigned 8-bit integer: u8.

Next, we need to initialize the grid.

3. Write function, use aids.  
[write aids]
[declare variables for rows and columns, cell_width]
[]
