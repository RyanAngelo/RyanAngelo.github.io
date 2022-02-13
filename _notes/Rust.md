---
layout: post
title: Rust
name: Rust Notes
---
Notes on Rust Development

{% include breadcrumbs.html %}

## Table of Contents

[Cargo](#cargo)

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
