# This is what your program look like so far


`main.rs`

```rust
// Dependencies go here
use sdl2::video::Window;
use sdl2::pixels::Color;
use sdl2::render::Canvas;
use sdl2::EventPump;
use sdl2::event::Event;
use sdl2::keyboard::Keycode;


// this function initializes the canvas
fn init<'a>(width: i32, height: i32) -> (Canvas<Window>, EventPump) {
    let sdl_context = sdl2::init().unwrap();
    let video_subsystem = sdl_context.video().unwrap();

    let window = video_subsystem
        .window("Canvas", width as u32 + 1, height as u32 + 1)
        .position_centered()
        .build()
        .unwrap();

    let mut canvas = window.into_canvas().present_vsync().build().unwrap();

    canvas.set_draw_color(Color::RGB(255, 255, 255));
    canvas.clear();
    canvas.present();

    let event_pump = sdl_context.event_pump().unwrap();
    (canvas, event_pump)
}

//Data types
struct Cell {
    red: u8,
    green: u8,
    blue: u8,
    // later :pixel_type: i32,
}

struct Grid {
    grid: Vec<Vec<Cell>>,
}

//creates a grid with ncells*ncells initialized with cell in a color
fn grid_init(nx_cells: i32, ny_cells: i32) -> Grid {
    let mut grid_vector = Vec::new();

    for row in 0..ny_cells {
        grid_vector.push(Vec::new());
        for _column in 0..nx_cells {
            grid_vector[row as usize].push(Cell {
                red: 35_u8,
                green: 15_u8,
                blue: 13_u8,
                // pixel_type: 0,
            });
        }
    }
    let grid = Grid { grid: grid_vector };

    grid
}

// this is main
fn main() {
    let canvas_width = 200;
    let canvas_height = 200;

    let (canvas, mut events) = init(canvas_width, canvas_height);

    'game: loop {
        for event in events.poll_iter() {

            match event {
                Event::Quit { .. }
                | Event::KeyDown {
                    keycode: Some(Keycode::Escape),
                    ..
                } => break 'game,

                _ => continue 'game,
            }
        }
        // canvas.set_draw_color(Color::RGB(0, 0, 0));
        // canvas.clear();
        // canvas.present();
    }

}

```
