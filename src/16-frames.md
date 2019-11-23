# Displaying the grid in Frames

For each frame, the grid is drawn by displaying each single cell as a rectangle.

In `fn main()`, right after we defined the variables for rows and columns, define a variable for `cell_width` and calculate its value.

`fn display_cell` converts row column values of a single Cell into x and y pixels and draws a rectangle in the specified color at the specified coordinate.

```rust
pub fn display_cell(
    renderer: &mut Canvas<Window>,
    row: u32,
    col: u32,
    grid_data: &Grid,
    cell_width: &u32,
) {
    let cell_height = cell_width;

    let grid = &grid_data.grid;

    let x = cell_width * col;
    let y = cell_width * row;

    //For now, we want random colors, to see what happens.
    // let cell_color = &grid[row as usize][col as usize];
    // let drawing_color = Color::RGB(cell_color.red, cell_color.green, cell_color.blue);

    let red: u8 = rand::random();
    let green: u8 = rand::random();
    let blue: u8 = rand::random();

    let drawing_color = Color::RGB(red, green, blue);

    renderer.set_draw_color(drawing_color);
    let square = renderer.fill_rect(Rect::new(x, y, *cell_width, *cell_height));
    match square {
        Ok(()) => {}
        Err(error) => println!("{}", error),
    }
}
```

`fn display_frame` displays the whole grid by repeatedly calling `fn display_cell` on every cell in the grid.

```rust
pub fn display_frame(
    renderer: &mut Canvas<Window>,
    grid: &Grid,
    nx_cells: &u32,
    ny_cells: &u32,
    cell_width: &u32,
) {


    renderer.set_draw_color(Color::RGB(0, 0, 0));
    renderer.clear();

    for row in 0..*ny_cells {
        for column in 0..*nx_cells {
            display_cell(renderer, row, column, &grid, &cell_width)
        }
    }
    renderer.present();
}
```

Add both of these functions to your program. Discuss, how the compare to `fn display_rectangle`. Then delete `fn display_rectangle`, as is not needed anymore.

Substitute the line that calls `fn display_rectangle` with the following line:

```rust
lib::display_frame(&mut canvas, &grid, &columns, &rows, &cell_width);
```

Run the program! Enjoy!
