# Week 2: A Simple Line Counter

Let’s build a very simple application to start. You will write an application that takes in a single filename or “-” (stdin). It will read in the file, then output the number of lines, and other various metrics related to the file’s line count.

We will learn:
* How to parse args from std::env
* How to read a file line by line, or as an entire string
* How to test our code

## Requirements

* Your program should compile safely using the 2021 edition of Rust.
* If an unexpected error occurs, the program should panic with a helpful message (don’t just use `unwrap()`).
* On success, the program should exit with a status code of 0.
* The program’s output should be exactly as follows (one string per line, with a trailing newline):

```
There are N lines of code in [FILENAME].
There are N empty lines in [FILENAME].
NN.NN% of the lines in [FILENAME] are empty.
```
