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

## Creating a New Project

First, create a new project for your application with the command `cargo new NAME_OF_MY_PROJECT`.
This will create a folder named whatever you may have provided as the positional argument of the
command **relative to your current working directory**. This means that if you ran this command in
the directory `/home/me`, it would be created as `/home/me/NAME_OF_MY_PROJECT`. This might end up
being a place that's difficult to reach with your graphical file browser -- be careful!

If you 

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

...

## Writing our Code

...

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
We have now run a Rust program!

## Building our Code

When we run `cargo run`, we produce a debug build of our software, meaning there's a lot of optimizations that were forewent
in the name of getting something working fast. Further, debug symbols are included. To build our program, we can just run
`cargo build`:

```
...
```

## Learning Rust

The most valuable resource for learning Rust is [The Book](https://doc.rust-lang.org/stable/book/).
