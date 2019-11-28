# Handling User Input

Any game needs to process the user's input in some form. Let's work on that next.

In ggez, there's a number of optional methods for input handling defined on the [`EventHandler`]
trait. While we've implemented that trait already, these methods are missing from our `impl`. That's
fine, since the trait provides default implementations of them that simply do nothing.

1. Implement the `key_down_event` method. Use `println!("{:?}", keycode);` to print the pressed key
   to the console.

<!-- Assumes `enum` and `match` already explained in the intro -->
2. The `keycode` argument is of type [`KeyCode`], which is an `enum`. Check its documentation to
   find out which variants we can work with. `match` on the key code and handle the 4 arrow keys.
   Print a unique string for each arrow key.

3. Extend the `match` to also handle the escape key. Make the escape key exit the game by calling
   [`ggez::event::quit`].

[`EventHandler`]: https://docs.rs/ggez/0.5.1/ggez/event/trait.EventHandler.html
[`KeyCode`]: https://docs.rs/ggez/0.5.1/ggez/input/keyboard/enum.KeyCode.html
[`ggez::event::quit`]: https://docs.rs/ggez/0.5.1/ggez/event/fn.quit.html
