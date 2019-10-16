# Initializing the Grid

## structs and vectors

Now that we have established a basic functionality, we will start drawing! As a base for our game, we will use a grid of cells. Using structs, we will define our own data types for them. [Explain structs].

1. The `Grid`-struct has one Field named `grid`. The Datatype are vectors of `Cell`s as in a vector. The items in the inner vector are rows, the items in the outer vector colums.

``` rust
struct Grid {
    grid: Vec<Vec<Cell>>,
}
```
2. Write your own struct for the Cell type. This datatype is used to define the color of a cell, so it needs fields for each RGB-value. The data type of the RGB-values is an unsigned 8-bit integer: u8.

Next, we need to initialize the grid.

3. Write function, use aids.  
