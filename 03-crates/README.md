# Week 3: Working with External Dependencies

Now that we’ve grown at least a little accustomed to Rust’s syntax, let’s get familiar with its
ecosystem of packages. The Rust standard library is known for being “to-the-point” compared to
languages like Go or Python, but that’s not a bad thing. There are many high-quality
community-maintained packages (called “crates”) that can do almost anything under the sun for
you. For our application, we will investigate the `clap` crate for argument parsing.

We will learn how to:
* Use dependencies from [crates.io](crates.io)
* Parse arguments using [clap](https://docs.rs/clap/latest/clap/)
* Basic introduction to macros
* Option to aggregate lines across all files or distinguish file types
* Use a hash table to keep track of different file types
* Format strings

## Your Task

In addition to the basic line counting program from the previous weeks, the following must be supported:
* The program should accept a single positional argument, a **directory**, and it should recursively count the lines of all the
files in the directory.
* Useful help message should be printed when run with `--help`.
* Print helpful error messages
* If run **with** the `-A` option, the program’s output should be exactly as follows for each filename extension (one string per line, with a trailing newline):

```
There are N lines of code in [EXTNAME] files.
There are N empty lines in [EXTNAME] files.
NN.NN% of the lines in [EXTNAME] files are empty.
```

* If run **without** the `-A` option, the program’s output should be exactly as follows (one string per line, with a trailing newline):

```
There are N lines of code.
There are N empty lines.
NN.NN% of the lines are empty.
```

## Depending on `clap`

Most Rust libraries (crates) that you will encounter are typically hosted on [crates.io](crates.io). These crates will also have documentation
available on [docs.rs](docs.rs). For the line counting program, we will use the popular [`clap`](https://crates.io/crates/clap) crate for command-line argument parsing.
The corresponding documentation for this crate is available [here](https://docs.rs/clap/latest/clap/).

To depend on `clap`, it is as simple as navigating to the `clap` crates.io [page](https://crates.io/crates/clap), copy one line of TOML (for example, `clap = "3.1.18"`), and pasting it into your `Cargo.toml` file under the dependencies section:

```toml
[dependencies]
clap = "3.1.18"
```

For most crates, that is all you need to do to let `cargo` know that your program is depending on it.
In this case, we actually want to enable a special `clap` feature, so it will look slightly different:

```toml
[dependencies]
clap = { version = "3.1.18", features = ["derive"] }
```

Then, you can use `clap` in your program like so:

```rust
use clap;

fn main() {
    // code that uses clap...
}
```

When you build and run your code, then `cargo` will automatically download and compile the dependencies.
The `clap` [documentation](https://docs.rs/clap/latest/clap/#example) provides many examples of how you can use it.
You can read about how to specify the exact version or version range of the package you want [here](https://doc.rust-lang.org/cargo/reference/specifying-dependencies.html).

## Introduction to Macros

To make coding CLIs easier, `clap` provides macros that generate Rust code at compile time.
For example, let's look at an example struct that you could write that supports `clap` argument parsing:

```rust
use clap::Parser;

#[derive(Parser, Debug)]
#[clap(author, version, about)]
struct Args {
    /// File name.
    file: String,

    /// Fun level.
    #[clap(short, long, default_value_t = 100)]
    fun: usize,
}
```

Let's walk through this step by step. The idea of the `clap` derive macro is to help generate a CLI based on
the fields in an user-defined struct. This struct is marked with the attributes `Parser` (to ensure that it
can parse CLI arguments), and `Debug` (to automatically provide a way to debug print out the struct).
Then, the `clap` attribute macro is used to tell it to encorporate author, version, and about information
int othe CLI. This information is automatically taken from the `Cargo.toml` file.

The struct itself has two fields, which will be automatically transformed into CLI arguments.
The first field is the file name, which is by default a required positional
argument.
The second field is the fun level, which is an optional named argument. The fun level has a default value of 100.
The cool thing about the macros that `clap` provides is that the doc comments (specified with `///`)
will actually be transformed into help messages! This illustrates the power of macros. Such a short piece of code
can generate an entire functional CLI.

More information about macros is available in the [book](https://doc.rust-lang.org/book/ch19-06-macros.html).

## Hash Tables for Each File Type

You should use a hash table to keep track of the number of lines corresponding to each file type.
For our purposes, the file type is just the extension. For example, `rs` is the file type of `main.rs`.
You can learn more about Rust `HashMap`s by looking at the [documentation](https://doc.rust-lang.org/std/collections/struct.HashMap.html).

Additionally, you should take a look at the following resources:
* [Documentation](https://doc.rust-lang.org/std/fmt/index.html) on formatting strings
* [Documentation](https://doc.rust-lang.org/std/fs/fn.read_dir.html) with example on how to recursively get all files in a directory
