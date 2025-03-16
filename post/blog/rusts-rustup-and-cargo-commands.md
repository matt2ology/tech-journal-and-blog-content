---
authors:
  - Matt2ology
categories:
  - blog
date: 2025-03-14T03:59:56-07:00
draft: true
notes: blog
related-notes:
tags:
  - rust
title: Rust's `rustup` and `cargo` Commands
---

## Rust's `rustup` and `cargo` Commands

<!-- [Propose edits or changes on GitHub](link to GitHub repo of file) -->

A quick self reference list to Rust's `rustup` and `cargo` commands.

`rustup`: Rust installation manager

### Creating a new project

With GIT version control

```sh
cargo new <projectName>
```

Without GIT version control

```sh
cargo new <projectName> --vcs none
```

### Build and run

You don't need to be in the "projectName/src" folder. As long as you're in the projectName
folder running: `cargo run` will compile (invoke `rustc`) and run the executable of your
program (placed in the subdirectory "../target/debug").

```sh
cargo run
```

### Remove previous debug build

```sh
cargo clean
```
