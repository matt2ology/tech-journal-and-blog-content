---
authors: Steve Klabnik and Carol Nichols
categories:
  - reference
date: 2025-01-21
draft: true

sources: kindle
media: books
notes: reference
tags: readwise, reference/books
title: Reference - Steve Klabnik and Carol Nichols - The Rust Programming Language
---
## The Rust Programming Language (Highlights)

![rw-book-cover](https://m.media-amazon.com/images/I/71aCEjlQBoL._SY160.jpg)

Source published date: None

## Highlights
### Location 1362

> This version of the text assumes you’re using Rust 1.62.0 (released 2022-06-30) or later with edition="2021" in the Cargo.toml file of all projects to configure them to use Rust 2021 edition idioms.
> \- [(Location 1362)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1362)

**Initial thought or note on:** [(Location 1362)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1362)
Run `rustc --version` in the command prompt: this command will output the version of Rust installed on your system if Rust is installed. If Rust is not installed, you will likely see an error message indicating that rustc is not recognized as a command. Currently I have: `rustc 1.68.0 (2c8cc3432 2023-03-06)`

### Location 1476

> An important part of the process of learning Rust is learning how to read the error messages the compiler displays: these will guide you toward working code. As such, we’ll provide many examples that don’t compile along with the error message the compiler will show you in each situation. Know that if you enter and run a random example, it may not compile! Make sure you read the surrounding text to see whether the example you’re trying to run is meant to error. In most situations, we’ll lead you to the correct version of any code that doesn’t compile.
> \- [(Location 1476)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1476)

**Initial thought or note on:** [(Location 1476)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1476)
Rust's robust and verbose error messages is also a means of support in either directing one what is the issue or provide a hint as to what is wrong with the code.

### Location 1497

> rustup, a command line tool for managing Rust versions and associated tools.
> \- [(Location 1497)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1497)

**Initial thought or note on:** [(Location 1497)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1497)
The alternative method to install Rust can be found there: https://forge.rust-lang.org/infra/other-installation-methods.html

### Location 1600

> Rust files always end with the .rs extension. If you’re using more than one word in your filename, the convention is to use an underscore to separate them. For example, use hello_world.rs rather than helloworld.rs.
> \- [(Location 1600)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1600)

**Initial thought or note on:** [(Location 1600)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1600)
The Rust file naming convention

### Location 1627

> it is always the first code that runs in every executable Rust program.
> \- [(Location 1627)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1627)

**Initial thought or note on:** [(Location 1627)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1627)
Question: is there a case that you'll have a Rust program that intentially doesn't run? Why is there an articulation that it "runs in every executable Rust program"?

### Location 1651

> end the line with a semicolon (;), which indicates that this expression is over and the next one is ready to begin. Most lines of Rust code end with a semicolon.
> \- [(Location 1651)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1651)

**Initial thought or note on:** [(Location 1651)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1651)
Question: How do you know when a line of Rust code requires a semicolon or not?

### Location 1682

> Just compiling with rustc is fine for simple programs, but as your project grows, you’ll want to manage all the options and make it easy to share your code. Next, we’ll introduce you to the Cargo tool, which will help you write real-world Rust programs.
> \- [(Location 1682)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1682)

**Initial thought or note on:** [(Location 1682)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1682)
Rust's solution to C language make files. Also draws inspiration from Python's package manager PIP.

### Location 1686

> Cargo is Rust’s build system and package manager. Most Rustaceans use this tool to manage their Rust projects because Cargo handles a lot of tasks for you, such as building your code, downloading the libraries your code depends on, and building those libraries. (We call the libraries that your code needs dependencies.)
> \- [(Location 1686)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1686)

**Initial thought or note on:** [(Location 1686)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1686)
A makefile and package manager all wrapped into one tool.

### Location 1748

> If you started a project that doesn’t use Cargo, as we did with the “Hello, world!” project, you can convert it to a project that does use Cargo. Move the project code into the src directory and create an appropriate Cargo.toml file.
> \- [(Location 1748)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1748)

**Initial thought or note on:** [(Location 1748)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1748)
Rust is not so restrictive to dis-allow others from adopting it's opinionated structure and quickly gain benifits from RUST tooling.

### Location 1833

> You’ll learn about let, match, methods, associated functions, external crates, and more!
> \- [(Location 1833)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1833)

### Location 1877

> To obtain user input and then print the result as output, we need to bring the io input/output library into scope. The io library comes from the standard library, known as std: use std::io;
> \- [(Location 1877)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1877)

**Initial thought or note on:** [(Location 1877)](https://readwise.io/to_kindle?action=open&asin=B0B7QTX8LL&location=1877)
like C/CPP one would need to import libraries to do user input.

