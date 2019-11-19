# Ownership and Borrowing

We're finally getting to something that is very exclusively Rusty: Ownership, Referencing and Borrowing. Ownership guarantees the memory safety of Rust. Each value has a variable, that is called its owner. There can only be one owner at a time. When the value goes out of scope, the value will be dropped.

1. Uncomment one `println!` statement at a time, to find out, where `s` is in scope und where it is not. Run the code in this window.
2. Why is `s` not in scope, after it moved into the function?

```rust, editable
fn main() {
    let s = String::from("hello");  
    //println!("{}", s)

    takes_ownership(s);

    //println!("{}", s)           

}
//println!("{}", s)

fn takes_ownership(some_string: String) {
    println!("{}", some_string);
}

```

So yeah, if you don't want to hand over the ownership of your value to the function, the function can borrow it. A borrowed value is indicated by the `&` operator.

```rust, editable
fn main() {
    let s = String::from("hello");  

    borrows_value(&s);

    println!("{}", s)           

}

fn borrows_value(some_string: &String) {
    println!("{}", some_string);
}

```
3. What happens, if the borrowed value is changed?

```rust, editable
fn main() {
    let s = String::from("hello");

    change(&s);
}

fn change(some_string: &String) {
    some_string.push_str(", world");
}

```

References (borrowed values) are immutable by default. To make the reference mutable, the variable has to be declared mutable, and &s changes to &mut s, same goes for &String. Try it!
But there are two restrictions:
* There can only be one mutable reference to a value!
* A value can not be borrowed mutable and immutable!


```rust

fn display_frame (
    renderer: &mut Canvas<Window>,
    canvas_width: &i32,
    canvas_height: &i32,

) {
    let red: u8 = rand::random();
    let green: u8 = rand::random();
    let blue: u8 = rand::random();

    renderer.clear();

    let drawing_color = Color::RGB(red, green, blue);
    renderer.set_draw_color(drawing_color);

    let square_definition = Rect::new(0, 0, *canvas_width as u32, *canvas_height as u32);
    let square = renderer.fill_rect(square_definition);
    match square {
        Ok(()) => {}
        Err(error) => println!("{}", error),

    renderer.present();
}

```

The function takes the canvas, as well as the canvas width and height as arguments. It does not return a value. In the body of the function, the variables red, green and blue are assigned random `u8` numbers.
The `clear()` method is called on the renderer, this clears the canvas. When, like in our case, the entire canvas is drawn over, this does not really matter, but it's a good habit, to think of this.
Then, the drawing color is defined. We use a function that is provided by `sdl2`, the function takes in three `u8` values and returns a color.
The method `set_draw_color()` is called on the renderer, with `drawing_color` as argument.

We create a new rectangle with it's minimum and maximum x and y values as arguments and bind it to the variable `square_definition`. This variable is then passed to the method `fill_rect()`. Our square is rendered and put into the backbuffer.

The last line updates the screen with all the rendering done since the last update.

Do you notice anything peculiar about some of the type declarations in this function?

Run the program.
