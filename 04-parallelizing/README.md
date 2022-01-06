# Week 4: Parallelizing Line Counting

Rust is a strong language for parallelizing computations. Our use case of enumerating lines of code
is easily parallelizable.

Using Rust’s standard library, we will:
* Allow multiple files to be processed in parallel
* Aggregate line counts across multiple threads

## Requirements
* Your program should adhere to the requirements outlined in v0.2.0.
* Your program should have an additional option “-j, --threads”, that takes an integer value
  (e.g., 4, 6, 8, etc.) which specifies the number of threads that the program will use to process
  files in parallel.
* Your program’s output should be deterministic. That is, its output between runs should be identical.
