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
* Useful help message should be printed when run with `--help`.
* Print helpful error messages
* If run **with** the `-A` option, the program’s output should be exactly as follows for each filename extension (one string per line, with a trailing newline):

```
There are N lines of code in [EXTNAME] files.
There are N empty lines in [EXTNAME] files.
NN.NN% of the lines in [EXTNAME] files are empty.
```

* If run **without** the -A option, the program’s output should be exactly as follows (one string per line, with a trailing newline):

```
There are N lines of code.
There are N empty lines.
NN.NN% of the lines are empty.
```

## Depending on `clap`

## Introduction to Macros

## Hash Tables for Each File Type


Additionally, you should take a look at the following resources:
* [Documentation](https://doc.rust-lang.org/std/fmt/index.html) on formatting strings
