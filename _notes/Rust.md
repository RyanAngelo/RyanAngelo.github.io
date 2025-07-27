---
layout: post
title: Rust Development Guide
name: Rust Development Guide
---
A comprehensive guide to Rust development, covering essential concepts, tools, and best practices.

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

## Cargo Commands

### Check Code Without Building
```bash
cargo check
```

### Release Build
```bash
cargo build --release
```

### Update Dependencies
```bash
cargo update
```

### Clean Build Artifacts
```bash
cargo clean
```

### Run Tests with Output
```bash
cargo test -- --nocapture    # Show println! output
cargo test -- --show-output  # Show all output
cargo test -- --test-threads=1  # Run tests sequentially
```

### Format Code
```bash
cargo fmt
```

### Check Code Style
```bash
cargo clippy
```

### Create Documentation
```bash
cargo doc  # Generate docs
cargo doc --no-deps  # Generate docs excluding dependencies
cargo doc --open  # Generate and open docs in browser
```

## Project Structure

```
my_project/
├── Cargo.toml
├── Cargo.lock
├── src/
│   ├── main.rs
│   ├── lib.rs
│   └── bin/
│       └── additional_binaries.rs
├── tests/
│   └── integration_tests.rs
└── examples/
    └── example_code.rs
```

## Common Attributes

```rust
// Testing
#[test]
#[should_panic]
#[ignore]

// Derive common traits
#[derive(Debug)]
#[derive(Clone, Copy)]
#[derive(PartialEq, Eq)]

// Visibility
#[pub]
#[pub(crate)]

// Conditional compilation
#[cfg(test)]
#[cfg(target_os = "linux")]
```

## Useful Macros

```rust
println!("Formatted print: {}", value);
format!("Create a String with {}", value);
vec![1, 2, 3];  // Create a vector
assert!(condition);
assert_eq!(left, right);
panic!("Error message");
```

## Common Type Conversions

```rust
// String conversions
String::from("literal");
"literal".to_string();
&String into &str;

// Number conversions
let x: i32 = "42".parse().unwrap();
let y = 42.to_string();

// Vector/Array conversions
let v: Vec<i32> = (1..4).collect();
let slice: &[i32] = &v[..];
```

## Error Handling Patterns

```rust
// Using Result
fn fallible() -> Result<Success, Error> {
    Ok(success_value)
}

// Using Option
fn maybe() -> Option<Value> {
    Some(value)
}

// Propagating errors
fn propagate() -> Result<T, E> {
    let x = something()?;
    Ok(x)
}

// Unwrap patterns
value.unwrap();  // Panics on None/Err
value.expect("Custom error message");
value.unwrap_or(default);
value.unwrap_or_else(|| expensive_computation());
```

## Memory Management

```rust
// Box - heap allocation
let boxed = Box::new(value);

// Rc - reference counting
use std::rc::Rc;
let shared = Rc::new(value);

// Arc - atomic reference counting
use std::sync::Arc;
let thread_safe = Arc::new(value);

// RefCell - interior mutability
use std::cell::RefCell;
let mutable = RefCell::new(value);
```

## Common Traits

```rust
// Display formatting
impl std::fmt::Display for MyType {
    fn fmt(&self, f: &mut std::fmt::Formatter) -> std::fmt::Result {
        write!(f, "MyType: {}", self.value)
    }
}

// Default values
impl Default for MyType {
    fn default() -> Self {
        MyType { value: 0 }
    }
}

// Clone and Copy
#[derive(Clone, Copy)]
struct MyType {
    value: i32,
}
