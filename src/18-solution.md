# Solution for the Snake

`snake.rs`

```rust
use crate::lib::types::{Cell, SnakeHead, Grid};

pub fn snake_init() -> SnakeHead {
    let snake = SnakeHead {
        row: 6,
        column: 6,
        color: Cell {
            red: 200_u8,
            green: 0_u8,
            blue: 100_u8,
        }
    };
    snake
}

pub fn snake_moves(snake: &mut SnakeHead, direction: (i32, i32)) -> SnakeHead {
    snake.row = snake.row + direction.0 ;
    snake.column = snake.column + direction.1;

    let new_snake = SnakeHead {
        row: snake.row,
        column: snake.column,
        color: Cell {
            red: 200_u8,
            green: 0_u8,
            blue: 100_u8,
        }
    };

    new_snake
}

pub fn draw_grid_with_snake(mut grid: Grid, snake: &SnakeHead) -> Grid {
    let color = Cell {
        red: snake.color.red,
        green: snake.color.green,
        blue: snake.color.green,
    };

    grid.grid[snake.row as usize][snake.column as usize] = color;
    grid
}
```

`types.rs`

```rust
pub struct SnakeHead {
    pub row: i32,
    pub column: i32,
    pub color: Cell,
}
```

Content of `'game` in `main.rs`

```rust
for event in events.poll_iter() {
    match event {
        Event::KeyDown {
            keycode: Some(Keycode::Up),
            ..
        } => {
            direction.0 = -1;
            direction.1 = 0;
        }

        Event::KeyDown {
            keycode: Some(Keycode::Down),
            ..
        } => {
            direction.0 = 1;
            direction.1 = 0;
        }

        Event::KeyDown {
            keycode: Some(Keycode::Left),
            ..
        } => {
            direction.1 = -1;
            direction.0 = 0;
        }

        Event::KeyDown {
            keycode: Some(Keycode::Right),
            ..
        } => {
            direction.1 = 1;
            direction.0 = 0;
        }

        Event::Quit { .. }
        | Event::KeyDown {
            keycode: Some(Keycode::Escape),
            ..
        } => break 'game,

        _ => continue 'game,
    }
}

snake = snake::snake_moves(&mut snake, direction);
grid = snake::draw_grid_with_snake(grid, &snake);
lib::display_frame(&mut canvas, &grid, &columns, &rows, &cell_width);
```
