# Week 3: External Dependencies

Now that we’ve grown at least a little accustomed to Rust’s syntax, let’s get familiar with its
ecosystem of packages. The Rust standard library is known for being “to-the-point” compared to
languages like Go or Python, but that’s not a bad thing. There are many high-quality
community-maintained packages (called “crates”) that can do almost anything under the sun for
you. For our application, we will investigate the `clap` crate for argument parsing.

We will:
* Use dependencies from crates.io
* Use attribute macros for CLI options
* Basic introduction to macros
* Option to aggregate lines across all files or distinguish file types
* Use a hash table to keep track of different file types

## Requirements

* Your program should compile safely using the 2021 edition of Rust.
* If an unexpected error occurs, the program should panic with a helpful message (don’t use `unwrap()`).
* On success, the program should exit with a status code of 0.
* The program should provide useful help output when run with `--help`.
* If run WITH the `-A` option, the program’s output should be exactly as follows for each filename extension (one string per line, with a trailing newline):

```
There are N lines of code in [EXTNAME] files.
There are N empty lines in [EXTNAME] files.
NN.NN% of the lines in [EXTNAME] files are empty.
```

* If run WITHOUT the -A option, the program’s output should be exactly as follows (one string per line, with a trailing newline):

```
There are N lines of code.
There are N empty lines.
NN.NN% of the lines are empty.
```
