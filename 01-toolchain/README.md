# Week 1: The Rust Toolchain

Rust has a highly integrated toolchain. The version of the Rust compiler you’re using, the version
of the package manager you’re using, and more are all widely controlled by a single command-line
application: `rustup`.

We will learn how to:
* Install `rustup`
* Use `cargo`
* Create a new project with Rust
* The difference between a Rust binary and a Rust library
* Basic workflow for compiling and running Rust programs

## Setting up our Development Environment

1. Install rustup by following the instructions given here: https://rustup.rs/
2. Install the latest stable version of Rust as the installation toolchain walks you through it.

More information is available [here](https://doc.rust-lang.org/book/ch01-01-installation.html).

## Creating a New Project

First, create a new project for your application with the command `cargo new NAME_OF_MY_PROJECT`.
This will create a folder named whatever you may have provided as the positional argument of the
command **relative to your current working directory**. This means that if you ran this command in
the directory `/home/me`, it would be created as `/home/me/NAME_OF_MY_PROJECT`. This might end up
being a place that's difficult to reach with your graphical file browser -- be careful!

Alternatively, you can initialize an existing folder or git repository with `cargo init .`.

More information is available [here](https://doc.rust-lang.org/book/ch01-03-hello-cargo.html).

## What's in a Rust Project?

To keep things consistent, let's create a sample project: `cargo new myproject`.

Let's take a look inside our folder to see what that command created for us:

```
$ find project
myproject
myproject/src
myproject/src/main.rs
# ...probably a bunch of .git stuff
myproject/Cargo.toml
```

Let's start with the top level: `Cargo.toml`.

```toml
[package]
name = "myproject"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]

```

This is our package manifest, containing all of the important information about what our package is and what it does.
Later on, this file will contain important information like which packages `myproject` depends on.

The file `myproject/src/main.rs` is the entry point of the program. By default, this currently contains only

```rust
fn main() {
    println!("Hello, world!");
}
```

## Running our Code

Rust is a **compiled language**, like C++. This means that to run your program, we first need to build it. Typically, this
would mean writing a `Makefile` or running some compiler commands to package all our source code up nicely. With Rust, this
is as easy as running `cargo run`:

```
$ cargo run
   Compiling example v0.1.0 (/home/me/projects/myproject)
    Finished dev [unoptimized + debuginfo] target(s) in 5.53s
     Running `target/debug/example`
Hello, world!
```

Depending on which operating system you're using, your output might vary a bit, but the important part is the "Hello, world!".
We now have a running Rust program!

## Learning Rust

The most valuable resource for learning Rust is [The Book](https://doc.rust-lang.org/stable/book/).

This [resource](https://fasterthanli.me/articles/a-half-hour-to-learn-rust) exists if you want to speedrun Rust syntax in 30 minutes.

A good way to familiarize yourself with Rust syntax is by looking at [Rust by Example](https://doc.rust-lang.org/rust-by-example/).

## Your Task
* Open a pre-designated file (eg., `example.txt`) and count lines in it
* Print out the number of lines

Take a look at the following resources to help you get started with this project:

* Rust by Example [page](https://doc.rust-lang.org/rust-by-example/std_misc/file/open.html) on opening files for reading.
* Rust by Example [page](https://doc.rust-lang.org/rust-by-example/std_misc/file/read_lines.html) on reading lines in a file.

Don't worry if you don't know exactly what is going on in each line of Rust code. The goal is for you to have the chance to
play around with some Rust code and get familiar with the syntax.
