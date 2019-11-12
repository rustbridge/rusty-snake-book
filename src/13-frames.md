# Displaying Frames

Each animation step is displayed in a new frame. For each frame, the grid is drawn by displaying each single cell as a rectangle. `sdl` offers methods to draw basic shapes, like rectangles, this needs to be imported. It also offers methods that convert our u8 values into RGB colors, that can be displayed.

```rust
use sdl2::rect::Rect;
use sdl2::pixels::Color;
```

Next, we will write a function, that converts row column values of a single Cell into x and y pixels and draws a rectangle in the specified color.
```rust
fn display_cell(
    renderer: Canvas<Window>,
    row: i32,
    col: i32,
    grid_data: Grid,
    cell_width: i32,
) {
    //cell cell_height is the same as cell_width
    //define a variable that is bound to the field grid of Grid
    //convert row and column values of this cell into x and y pixels
    //define a variable that is bound to the Cell.
    //define a variable drawing_drawing color, calling Color::RGB(red, green, blue)
}
```

Add both of these functions to your program.

```rust



pub fn display_cell(
    renderer: &mut Canvas<Window>,
    row: i32,
    col: i32,
    grid_data: &Grid,
    cell_width: &i32,
) {
    let cell_height = cell_width;

    let grid = &grid_data.grid;

    let x = cell_width * col;
    let y = cell_width * row;

    let cell_color = &grid[row as usize][col as usize];
    let drawing_color = Color::RGB(cell_color.red, cell_color.green, cell_color.blue);

    renderer.set_draw_color(drawing_color);
    let square = renderer.fill_rect(Rect::new(x, y, *cell_width as u32, *cell_height as u32));
    match square {
        Ok(()) => {}
        Err(error) => println!("{}", error),
    }
}

//displays the whole grid by repeatedly calling display_cell on every cell
pub fn display_frame(
    renderer: &mut Canvas<Window>,
    grid: &Grid,
    nx_cells: &i32,
    ny_cells: &i32,
    cell_width: &i32,
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
