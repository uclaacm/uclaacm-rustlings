# Week 2: A Simple CLI Line Counter

This week's lesson is centered around building a simple application that takes input from the command-line.
In summary, you will write an application that takes in a single filename or "-" (stdin).
It will read in the file, then output the number of lines in the file.

We will learn:
* Reading a file line-by-line in Rust
* Parsing command-line arguments using `std::env`

## Your Task

* Create a program that takes in a single filename or "-" (for stdin) as the command-line argument. (Note: don't use any external crates, use `std::env`).
* The program should read the file (or stdin), counting the number of lines.
* The program should print a line with a single number, the total number of lines in the file.
* Print descriptive error messages! Don't just use `unwrap()`, but instead `expect()`.

To accomplish this task, you should take a look at the following resources:
* [Documentation](https://doc.rust-lang.org/std/env/fn.args.html) on `std::env::args()`
* This [blog post](https://kerkour.com/rust-read-file) on different ways of reading from a file
* Rust by Example [page](https://doc.rust-lang.org/rust-by-example/std_misc/file/open.html) on opening a file
* This [documentation](https://doc.rust-lang.org/std/iter/trait.Iterator.html#tymethod.next) on Rust iterators (specifically `next()` and `skip()`)
* Documentation on [`Result`](https://doc.rust-lang.org/std/result/) and [`Option`](https://doc.rust-lang.org/std/option/), which are important types for representing errors or "nulls"
