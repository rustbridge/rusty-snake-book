# Multithreading

Rust is famous for its safe and easy way to write multithreaded programs. We don't need this program to be multithreaded yet, but it comes with a handy sleep mode, that we need.

To spawn a thread, add these lines before `'game`:

```rust
thread::spawn(move || {
    // some work here
    });
```
Inside, at the end of `'game`, add this line:

```rust
thread::sleep(time::Duration::from_millis(800));
```
`'game` will now sleep 800 milliseconds, before starting over.
