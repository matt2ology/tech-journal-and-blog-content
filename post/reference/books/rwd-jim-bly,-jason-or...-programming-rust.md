---
authors: Jim Blandy, Jason Orendorff, and Leonora F. S. Tindall
categories:
  - reference
date: 2025-03-17
draft: true

sources: kindle
media: books
notes: reference
tags: readwise, reference/books
title: Reference - Jim Blandy, Jason Orendorff, and Leonora F. S. Tindall - Programming Rust
---
## Programming Rust (Highlights)

![rw-book-cover](https://m.media-amazon.com/images/I/91syf9W6vpS._SY160.jpg)

Source published date: None

## Highlights
### Location 42

> systems programming is resource-constrained programming. It is programming when every byte and every CPU cycle counts.
> \- [(Location 42)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=42)

**Initial thought or note on:** [(Location 42)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=42)
Think budget, edge, embedded, IOT devices; and, operating systems, device drivers of all kinds, filesystems, databases, cryptography, media codecs, media processing, memory management, text rendering, networking, virtualization and software containers, video games, and the alike...

### Location 47

> you’ll find that Rust is something exceptional: a new tool that eliminates major, well-understood problems that have plagued a whole industry for decades.
> \- [(Location 47)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=47)

### Location 53

> Rust’s speed, concurrency, and safety.
> \- [(Location 53)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=53)

**Initial thought or note on:** [(Location 53)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=53)
The benifits of using Rust

### Location 69

> Traits are like interfaces in Java or C#. They’re also the main way Rust supports integrating your types into the language itself.
> \- [(Location 69)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=69)

### Location 70

> traits support operator overloading,
> \- [(Location 70)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=70)

### Location 207

> The Rust language makes you a simple promise: if your program passes the compiler’s checks, it is free of undefined behavior.
> \- [(Location 207)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=207)

**Initial thought or note on:** [(Location 207)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=207)
This is baked into the language though concepts like ownership allows one to program with the compiler working alongside with you to make sure that any and all possible errors are delt with and is properly managed.

### Location 219

> Concurrency is notoriously difficult to use correctly in C and C++.
> \- [(Location 219)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=219)

### Location 220

> Developers usually turn to concurrency only when single-threaded code has proven unable to achieve the performance they need.
> \- [(Location 220)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=220)

**Initial thought or note on:** [(Location 220)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=220)
Although true... A majority of applications run single threaded; for, the most optimal amount of threads to run is one. Multitasking is a lie.

### Location 223

> the same restrictions that ensure memory safety in Rust also ensure that Rust programs are free of data races.
> \- [(Location 223)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=223)

### Location 236

> Systems programming is often concerned with pushing the machine to its limits.
> \- [(Location 236)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=236)

### Location 239

> operating systems: the kernel should make the machine’s resources available to user programs, not consume them itself.
> \- [(Location 239)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=239)

**Initial thought or note on:** [(Location 239)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=239)
When writing code one should program in a manner that is not only effective but also effiecent. One's program in the system should not consume any more resources to reasonably perform the task. Don't be selfish. Share resources for ultimately you're not shipping your system. You are building solutions for all to use.

### Location 247

> Rust’s package manager and build tool, Cargo, makes it easy to use libraries published by others on Rust’s public package repository, the crates.io website. You simply add the library’s name and required version number to a file, and Cargo takes care of downloading the library, together with whatever other libraries it uses in turn, and linking the whole lot together.
> \- [(Location 247)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=247)

### Location 252

> also designed to support collaboration: Rust’s traits and generics let you create libraries with flexible interfaces so that they can serve in many different contexts.
> \- [(Location 252)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=252)

### Location 254

> Rust’s standard library provides a core set of fundamental types that establish shared conventions for common cases, making different libraries easier to use together.
> \- [(Location 254)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=254)

### Location 286

> a tool for managing Rust installations, like RVM for Ruby or NVM for Node. For example, when a new version of Rust is released, you’ll be able to upgrade with zero clicks by typing rustup update.
> \- [(Location 286)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=286)

**Initial thought or note on:** [(Location 286)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=286)
`rustup`: Rust installation manager

### Location 296

> cargo is Rust’s compilation manager, package manager, and general-purpose tool. You can use Cargo to start a new project, build and run your program, and manage any external libraries your code depends on.
> \- [(Location 296)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=296)

**Initial thought or note on:** [(Location 296)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=296)
`cargo` handles compilation, package management, provides the initial setup for a new project, and manages external dependency libraries

### Location 299

> rustc is the Rust compiler. Usually we let Cargo invoke the compiler for us, but sometimes it’s useful to run it directly.
> \- [(Location 299)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=299)

**Initial thought or note on:** [(Location 299)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=299)
Compile source code without extra steps.

### Location 301

> rustdoc is the Rust documentation tool. If you write documentation in comments of the appropriate form in your program’s source code, rustdoc can build nicely formatted HTML from them. Like rustc, we usually let Cargo run rustdoc for us.
> \- [(Location 301)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=301)

**Initial thought or note on:** [(Location 301)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=301)
Just build the documation Rust documentation tool.

### Location 304

> As a convenience, Cargo can create a new Rust package for us, with some standard metadata arranged appropriately: $ cargo new hello      Created binary (application) `hello` package This command creates a new package directory named hello, ready to build a command-line executable.
> \- [(Location 304)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=304)

**Initial thought or note on:** [(Location 304)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=304)
The standard metadata is stored within the Cargo.toml file. It describes basic information on the Rust package and its dependencies. For example: ```toml [package] name = "hello" version = "0.1.0" edition = "2021" [dependencies] ```

### Location 329

> Cargo has set up our package for use with the git version control system, creating a .git metadata subdirectory and a .gitignore file. You can tell Cargo to skip this step by passing --vcs none to cargo new on the command line.
> \- [(Location 329)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=329)

**Initial thought or note on:** [(Location 329)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=329)
```sh cargo new <projectName> --vcs none ```

### Location 342

> We can invoke the cargo run command from any directory in the package to build and run our program: $ cargo run
> \- [(Location 342)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=342)

**Initial thought or note on:** [(Location 342)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=342)
You don't need to be in the "projectName/src" folder. As long as you're in the projectName folder running: `cargo run` will compile (invoke `rustc`) and run the executable of your program (placed in the subdirectory "../target/debug").

### Location 359

> cargo clean
> \- [(Location 359)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=359)

**Initial thought or note on:** [(Location 359)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=359)
The command ```sh cargo clean ``` "Cleans" out the previous compiled build of your program stored in (../target/debug/projectName).

### Location 362

> Rust’s syntax is deliberately unoriginal. If you are familiar with C, C++, Java, or JavaScript, you can probably find your way through the general structure of a Rust program.
> \- [(Location 362)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=362)

**Initial thought or note on:** [(Location 362)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=362)
Rust adopts/follows the C-family like syntax/language.

### Location 391

> The fn keyword (pronounced “fun”) introduces a function.
> \- [(Location 391)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=391)

**Initial thought or note on:** [(Location 391)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=391)
`fn` keyword, pronounced "fun", is reserved for creating functions.

### Location 396

> Rust’s machine integer type names reflect their size and signedness: i32 is a signed 32-bit integer; u8 is an unsigned 8-bit integer (used for “byte” values), and so on. The isize and usize types hold pointer-sized signed and unsigned integers, 32 bits long on 32-bit platforms, and 64 bits long on 64-bit platforms.
> \- [(Location 396)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=396)

**Initial thought or note on:** [(Location 396)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=396)
Rust makes you declaratively define if your integers are signed or not, and their bit-size (e.g. `i64` for signed 64 bit size integers; `u32` for unsigned 32 bit integers; and for byte values `u8` is used for that). Both `isize` (signed integers) and `usize` (unsigned integers) hold pointer-sized signed and unsigned integers that are of 32 or 64 bit long respective to it's targeted bit-size platform.

### Location 400

> Rust also has two floating-point types, f32 and f64, which are the IEEE single- and double-precision floating-point types, like float and double in C and C++.
> \- [(Location 400)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=400)

**Initial thought or note on:** [(Location 400)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=400)
Rust's floating-point types, `f32` and `f64`, follows the IEEE standard for single- and double-precision; just as, in C and CPP for `float` and `double`

### Location 402

> By default, once a variable is initialized, its value can’t be changed, but placing the mut keyword (pronounced “mute,” short for mutable) before the parameters n and m allows our function body to assign to them. In practice, most variables don’t get assigned to; the mut keyword on those that do can be a helpful hint when reading code.
> \- [(Location 402)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=402)

**Initial thought or note on:** [(Location 402)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=402)
All variables, by default, are "constant" and are not allowed to be changed/modified. To allow variables you define to be mutable (it's value subjectable to change or modification) you'd need to place the keyword `mut` prior to the variable name and the variable signedness-bit-length; for example, from immutable signed 32-bit variable `vara: i32` to mutable signed 32-bit variable `mut vara: i32`.

### Location 409

> Rust’s assert! checks that its argument is true, and if it is not, terminates the program with a helpful message including the source location of the failing check; this kind of abrupt termination is called a panic. Unlike C and C++, in which assertions can be skipped, Rust always checks assertions regardless of how the program was compiled.
> \- [(Location 409)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=409)

**Initial thought or note on:** [(Location 409)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=409)
Assertions can be made within one's program via the micro `assert!` (e.g. `assert!(foobar != 0)`). Regardless how the program is compiled, via rustc or cargo, all assertions are tested if true otherwise if false it will produce the location of the failed assertion and an error message describing why the assertion (`assert!`) failed. When an assertion fails, the compilation of the code is then terminated: this is called a "panic".

### Location 412

> There is also a debug_assert! macro, whose assertions are skipped when the program is compiled for speed.
> \- [(Location 412)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=412)

**Initial thought or note on:** [(Location 412)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=412)
`debug_assert!(foobar != 0)`

### Location 417

> Unlike C and C++, Rust does not require parentheses around the conditional expressions, but it does require curly braces around the statements they control.
> \- [(Location 417)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=417)

### Location 418

> A let statement declares a local variable,
> \- [(Location 418)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=418)

**Initial thought or note on:** [(Location 418)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=418)
Used only in functions. Rust infers the variable type given the surrounding context of the function's parameters and return type; however, if you'd like to be declarative and verbose as to what that type your `let`, local, variable is you can do so in the following fashion: `let varableName: u64 = foobarc`

### Location 428

> If a function body ends with an expression that is not followed by a semicolon, that’s the function’s return value. In fact, any block surrounded by curly braces can function as an expression.
> \- [(Location 428)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=428)

**Initial thought or note on:** [(Location 428)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=428)
```rust { println!("The value of x is: "); x } ```

### Location 435

> It’s typical in Rust to use this form to establish the function’s value when control “falls off the end” of the function, and use return statements only for explicit early returns from the midst of a function.
> \- [(Location 435)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=435)

**Initial thought or note on:** [(Location 435)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=435)
`return` statements are used for when the programmer explicitly want to return early within a function; otherwise, you'd let your function execute, process, and when the function is done (no further operations are needed) you then return the value of the function.

### Location 462

> The #[test] atop the definition marks test_gcd as a test function, to be skipped in normal compilations, but included and called automatically if we run our program with the cargo test command. We can have test functions scattered throughout our source tree, placed next to the code they exercise, and cargo test will automatically gather them up and run them all.
> \- [(Location 462)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=462)

**Initial thought or note on:** [(Location 462)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=462)
Native testing can be done anywhere within the src folder. Rust's `cargo` will agregate all of them when running the command `cargo test`. All tests are excluded from compilation of code.

### Location 466

> The #[test] marker is an example of an attribute. Attributes are an open-ended system for marking functions and other declarations with extra information, like attributes in C++ and C#, or annotations in Java.
> \- [(Location 466)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=466)

**Initial thought or note on:** [(Location 466)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=466)
Is this similar to a "decorator" in Python?

### Location 527

> A trait is a collection of methods that types can implement.
> \- [(Location 527)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=527)

**Initial thought or note on:** [(Location 527)](https://readwise.io/to_kindle?action=open&asin=B0979PWD4Z&location=527)
Types as in varable types: `u8`, `u32`, `u64`, `i32`, `i64`, `f32`, `f64`

