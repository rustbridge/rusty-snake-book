# Installation

## Standard Installation of the Rust Compiler and Tools

### Linux and MacOS Users

For these platforms, it is recommended to use the [Official Rust Installation Process](https://rustup.rs/) via `rustup.rs`. When asked, the default settings (including the `stable` compiler) are suitable for this course.

This will process will install a number of tools required for this course, including `rustc`, `cargo`, and `rustup`.

### Windows Users

Windows Users may need to install additional tools. Please refer to the [following guide](https://doc.rust-lang.org/book/ch01-01-installation.html#installing-rustup-on-windows) for installation instructions for Windows.

## Simple DirectMedia Layer

Simple DirectMedia Layer is a cross-platform development library designed to provide low level access to audio, keyboard, mouse, joystick, and graphics hardware via OpenGL and Direct3D. It is written in C, and we will only use Rust bindings later on, you need to install the C library separately.

### MacOS

```shell
brew install sdl2
```

### Ubuntu

```shell
sudo apt-get install libsdl2-dev
```

### Windows

Follow the instructions [here](https://github.com/Rust-SDL2/rust-sdl2#windows-msvc), following the steps "For Rustup users".

### Other Operating Systems

[Download](https://www.libsdl.org/download-2.0.php) and install the development library according to your system.
