---
layout: post
title: Rust
name: Rust Notes
---
Notes on Rust Development

{% include breadcrumbs.html %}

## Table of Contents

[Cargo](#cargo)

[Variables](#variables)

## Cargo

### Starting a new project

`cargo new project_name`

### Building

`cargo build`

### Running

`./target/debug/project_name`

### Build and Run

`cargo run`

### Generating Documentation

This will generate documentation and open it up in the browser. File is located in project-name/target/doc/project-name/index.html

`cargo doc --open`

### cargo test

Cargo looks for tests in each of the src files and /tests.
/tests should be used for integration style tests, while the te sts in the src files should be unit tests.

`cargo test`

You can run a specific test:

`cargo test mytest`

This will run any test that has mytest in the name of the test.

### cargo dependencies

Dependencies can be added to the Cargo.toml in the dependencies section.
The versions that are used for dependencies use [SemVer](https://semvar.org).

## Variables

In Rust, variables are immutable by default.
Adding mut before the variable name let's the variable be mutable.

```rust
let oranges = 5;
let mut oranges = 5;
```

'&' indicates that a variable is a reference.

Shadowing the value of a variable means that a variable name is reused rather than making it so that two unique variables need to created.

```rust
let mut _mutable = 12;
_mutable = 21;
let _mutable = true;
```

## Error Handling

In Rust, the question mark ? is an operator used for error handling. When you see line?, it is shorthand for a pattern where an operation that could potentially fail (in this case, reading a line from a file) is attempted, and if the operation is successful, the value is returned. However, if the operation results in an error, the error is returned from the current function.
