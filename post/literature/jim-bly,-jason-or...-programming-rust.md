---
authors:
  - Matt2ology
categories:
  - literature
date: 2025-03-17T00:11:49-07:00
draft: true
media:
notes: literature
related-notes:
tags:
  - literature/book
title: Literature - O'Reilly Programming Rust
---

## Literature note: jim-bly,-jason-or...-programming-rust

> **Summary:**

[**Link to reference note**]({{< ref "/post/reference/books/rwd-jim-bly,-jason-or...-programming-rust.md" >}})

## Key Ideas

<!-- Idea 1: Key point or insights written in your own words -->

1.

## Chapters

### **Introduction:** Systems Programmers Can Have Nice Things

#### Rust Shoulders the Load for you

The rust compiler is very precise and "nit-picky" - it can be viewed as your more senior
developer friend calling out common errors and possible undefined behaviors made
in your code; of course, your friend can't predict and advice you from all bugs and errors,
but you'll find Rust to be safe and pleasant to use as you'll have the basic and common
bugs and errors caught early on than later producing behaviors you did not anticipate.

#### Parallel Programming is Tamed

The same strict memory usage and allocation enforcement ensures that Rust programs
are free from data races when implementing multithreaded applications; on the same
token, it argues and promotes to the developer to leverage parallelism, for it to be treated
as a last resort optimization on modern machines.

As a result, Rust is a great language to learn and fully utilize the full feature set of modern
multi-core machines.

The Rust ecosystem not only has the usual concurrency privatives, for it also helps distribute
work loads evenly across pools of processors via lock-free synchronization mechanisms like:
Read-Copy-Update, and more.

#### And Yet Rust Is Still Fast

System programming, by nature, imposes onto the programmer to be as efficient as they
can, for most applications in their field requires their software to be pushed to its limits.

For example, video games of the triple A class titles is already resource intensive, so one
should write code not to consume any more resources to execute any particular task.

Even when most consumer systems has access to more than 2 GB of ram one should be
mindful of the user as that it's not only your software that is running but various others,
and memory should released as soon as it's no longer in need.

No, one, programmer can be on-top of memory management; for this reason,
it's a feature, not a bug, that the compiler forces the programmer to be explicit and
intentional of their usage and allocation of memory.

Rust is designed with strict rules and defaults to support one's effort to direct how and
when to use both compute and memory resources to it's fullest.

#### Rust Makes Collaboration Easier

Rust's package manager, Cargo, pulls from Rust's public package repository.
Cargo is also a build tool that takes the library's name and version number,
takes care the download, and links everything together.

### **Introduction:** A Tour of Rust

The authors recommend to follow the instructions described here <https://rustup.rs/>
to install Rust; however, one can also install Rust via the prebuilt packages shared
on the Rust website.

#### `rustup` and Cargo

`rustup` is a version management tool for Rust installations.
The power in `rustup` is that when a new version of Rust is released
running the following command

```sh
rust update
```

updates are handled without further input from you, the user, but do make sure you
are connected to the internet when running the command.

Validate installation was successful

```sh
cargo --version
rustc --version
rustdoc --version
```

- **`cargo`**: handles compilation, package management, provides the initial setup for a new project, and manages external dependency libraries.
- **`rustc`**: the rust compiler. Sometimes we just want to simply compile source code without the additional steps that `cargo` runs to compile source code.
- **`rustdoc`**: much like `rustc` sometimes we just want to build documentation from our formatted comments in code without compiling source code. `rustdoc` will take our comments from code and build out an HTML documentation page.

Cargo is a great general purpose tool that does various typical/routine tasks;
like, cleaning-up (removing) the previous compiled build of your program stored in
(`../target/debug/projectName`).

```sh
cargo clean
```

#### Rust Functions

Rust adopts/follows the C-like family syntax

Rust makes you declaratively define if your integers are signed or not, and their bit-size
(e.g. `i64` for signed 64 bit size integers; `u32` for unsigned 32 bit integers; and for byte
values `u8` is used for that). Both `isize` (signed integers) and `usize` (unsigned integers)
hold pointer-sized signed and unsigned integers that are of 32 or 64 bit long respective to
it's targeted bit-size platform.

Rust's floating-point types, `f32` and `f64`, follows the IEEE standard for single- and double-
precision; just as, in C and CPP for `float` and `double`.

All variables, by default, are "constant" and are not allowed to be changed/modified. To allow variables you define to be mutable (it's value subjectable to change or modification) you'd need to place the keyword `mut` prior to the variable name and the variable signedness-bit-length; for example, from immutable signed 32-bit variable `vara: i32` to mutable signed 32-bit variable `mut vara: i32`.

Assertions can be made within one's program via the micro `assert!` (e.g. `assert!(foobar != 0)`). Regardless how the program is compiled, via `rustc` or `cargo`, all assertions are tested if true otherwise if false it will produce the location of the failed assertion and an error message describing why the assertion (`assert!`) failed. When an assertion fails, the compilation of the code is then terminated: this is called a "panic".

With that said you can use `debug_assert!` (e.g. `debug_assert!(foobar != 0)`) to skip assertions when compiling for speed.

Unlike C and CPP, Rust does not require parentheticals around the conditional expression, but it does require the curly braces around the body of the condition.

```rust
while vara != 0 {
    ...
}
```

```rust
if vara > varb {
    ...
}
```

Used only in functions. Rust infers the variable type given the surrounding context of the function's parameters and return type. In this case Rust infers that the variable `t` is an unsigned 64-bit integer (i.e. `u64`).

```rust
fn gdc(mut n: u64, mut m: u64) -> u64{
    assert!(n !=0 && m !=0);
    while m != 0 {
        if m < n {
            let t = m;
            m = n;
            n = t;
        }
        m = m % n;
    }
    n
}

fn main() {
    println!("Hello, world!");
    let x = gdc(5, 15);
    println!("{}", x);
    // Output: 5
}
```

However, if you'd like to be declarative and verbose as to what that type your `let`, local, variable is you can do so in the following fashion:

```rust
let varableName: u64 = foobard
```

Rust has a `return` statement, but by convention any function body or block of code with curly braces that has an expression that doesn't have a semicolon (i.e. `;`) is the function or block of code's return value

```rust
{
    let x = 5
    println!("The value of x is: ");
    x
    // Output: 5
}
```

`return` statements are used for when the programmer explicitly want to return early within a function; otherwise, you'd let your function execute, process, and when the function is done (no further operations are needed) you then return the value of the function.

#### Writing and Running Unit Tests

An "attribute", `#[test]`, is prepended above the test function. "Attributes" marks functions
and other declarations with additional information as done in C/CPP, or annotations in Java.

```rust
#[test]
fn test_myfunction(){
    assert_eq!(myfunction(parama, paramb, paramc))
    assert_eq!(myfunction(vara, varb, varc))
}
```

Attributes in Rust controls

- Compiler warnings
- Code style checks
- Conditional code inclusion (like in C/CPP's `#ifdef`): dictate how Rust interacts with code written in other languages

Native testing can be done anywhere within the src folder. Rust's `cargo` will aggregate all of them when running the command `cargo test`. All tests are excluded from compilation of code.

#### Handling Command-Line Arguments

```rust
use std::str::FromStr;
use std::env;
```

#### Serving Pages to the Web

### Fundamental Types

#### Fixed-Width Numeric Types

#### The bool Types

#### Characters

#### Tuples

#### Pointer Types

#### Arrays, Vectors, and Slices

#### String Types

#### Type Aliases

#### Beyond the Basics

### **Core Concept:** Ownership and Moves

#### Ownership

#### Moves

#### Copy Types: The Exception to Moves

#### Rc and ARC: Shared Ownership

### **Core Concept:** References

#### Reference to values

#### Working with References

#### Reference Safety

#### Sharing Versus Mutation

#### Taking Arms Against a Sea of Objects

### **Basics of the Language:** Expressions

#### An Expression Language

#### Precedence and Associativity

#### Blocks and Semicolons

#### Declarations

#### if and match

#### if let

#### Loops

#### Control Flow in Loops

#### return Expressions

#### Why Rust Has loop

#### Function and Method Calls

#### Fields and Elements

#### Reference Operators

#### Arithmetic, Bitwise, Comparison, and Logical Operators

#### Assignment

#### Type Casts

#### Closures

#### Onward

### **Basics of the Language - Don't Skip:** Error Handling

#### Panic

##### Unwinding

##### Aborting

#### Result

##### Catching Errors

##### Propagating Errors

##### Working with Multiple Error Types

##### Dealing with Errors That "Can't Happen"

##### Ignoring Errors

##### Handling Errors in `main()`

##### Declaring a Custom Error Type

##### Why Results?

### **Basics of the Language:** Creates and Modules

#### Crates

##### Editions

##### Build Profiles

#### Modules

##### Nested Modules

##### Modules in Separate Files

##### Paths and Imports

##### The Standard Prelude

##### Making use Declaration pub

##### Making Strict Fields pub

##### Static and Constants

#### Turning a Program into a Library

#### The src/bin Directory

#### Attributes

#### Testing and Documentation

##### Integration Tests

##### Documentation

##### Doc-Tests

#### Specifying Dependencies

##### Versions

##### Cargo.lock

#### Publishing Crates to crates.io

#### Workspaces

#### More Nice Things

### **Basics of the Language:** Structs

#### Named-Field Structs

#### Tuple-Like Structs

#### Unit-Like Structs

#### Stuct Layout

#### Defining Methods with `impl`

##### Passing Self as a Box, Rc, or Arc

##### Type-Associated Functions

#### Associated Consts

#### Generic Structs

#### Generic Structs with Lifetime Parameters

#### Generic Structs with Constant Parameters

#### Deriving Common Traits for Struct Types

#### Interior Mutability

### **Basics of the Language:** Enums and Patterns

#### Enums

##### Enums with Data

##### Enums in Memory

##### Rich Data Structures Using Enums

##### Generic Enums

#### Patterns

##### Literals, Variables, and Wildcards in Patterns

##### Tuple and Struct Patterns

##### Array and Slice Patterns

##### Reference Patterns

##### Match Guards

##### Matching Multiple Possibilities

##### Binding with `@` Patterns

##### Where Patterns Are Allowed

##### Populating a Binary Tree

#### The Big Picture

### **Core Concept:** Traits and Generics

Understanding traits and generics opens you to the rest of the book

#### Using Traits

##### Traits Objects

##### Generic Functions and Type Parameters

##### Which to Use

#### Defining and Implementing Traits

##### Default Methods

##### Traits and Other People's Types

##### Self in Traits

##### Subtraits

##### Type-Associated Functions

#### Fully Qualified Method Calls

#### Traits That Define Relationships Between Types

##### Associated Types (or How Iterators Work)

##### Generic Traits (or How Operator Overloading Work)

##### impl Trait

##### Associated Consts

#### Reverse-Engineering Bounds

#### Traits as a Foundation

### Operator Overloading

#### Arithmetic and Bitwise Operators

##### Unary Operators

##### Binary Operators

##### Compound Assignment Operators

#### Equivalance Comparisons

#### Ordered Comparisons

#### Index and IndexMut

#### Other Operators

### Utility Traits

#### Drop

#### Sized

#### Clone

#### Copy

#### Deref and DerefMut

#### Default

#### AsRef and AsMut

#### Borrow and BorrowMut

#### From and Into

#### TryFrom and TryInto

#### ToOwned

#### Borrow and ToOwned at work: The Humble Cow

### **Power Tool:** Closures

#### Capturing Variables

##### Closures That Borrow

##### Closures That Steal

#### Function and Closure Types

#### Closure Performance

#### Closure and Safety

##### Closures That Kill

##### FnOnce

##### FnMut

##### Copy and Clone for Closures

#### Callbacks

#### Using Closures Effectively

### **Power Tool:** Iterators

#### The Iterator and Intolterator Traits

#### Creating Iterators

##### `iter` and `iter_mute` Methods

##### intolterator Implementations

##### from_fn and successors

##### drain Methods

##### Other Iterator Sources

#### Iterator Adaptors

##### map and filter

##### filter_map and flat_map

##### flatten

##### take and take_while

##### skip and skip_while

##### peekable

##### fuse

##### Reversible Iterator and rev

##### inspect

##### chain

##### enumerate

##### zip

##### by_ref

##### cloned, copied

##### cycle

#### Consuming Iterators

##### max, min

##### max_by, min_by

##### max_by_key, min_by_key

##### Comparing Item Sequences

##### any and all

##### position, rposition, and ExactSizeIterator

##### fold and rfold

##### try_fold and try_rfold

##### nth, nth_back

##### last

##### find, rfind, and find_map

##### Building Collections: collect and FromIterator

##### The Extend Trait

##### partition

##### for_each and try_for_each

#### Implementing Your Own Iterators

### Collections

#### Overview

#### `Vec<T>`

##### Accessing Elements

##### Iteration

##### Growing and Shrinking Vectors

##### Joining

##### Splitting

##### Swapping

##### Filling

##### Sorting and Searching

##### Comparing Slices

##### Random Elements

##### Rust Rules Out Invalidation Errors

#### `VecDeque<T>`

#### `BinaryHeap<T>`

#### `HashMap<K,V>` and `BTreeMap<K,V>`

##### Entries

##### Map Iteration

#### `HashSet<T>` and `BTreeSet<T>`

##### Set Iteration

##### When Equal Values Are Different

##### Whole-Set Operations

#### Hashing

#### Using a Custom Hashing Algorithm

#### Beyond the Standard Collections

### Strings and Text

#### Some Unicode Background

##### ASCII, Latin-1, Unicode

##### UTF-8

##### Text Directionality

#### Characters (char)

##### Classifying Characters

##### Handling Digits

##### Case Conversion for Characters

##### Conversions to and from Integers

#### String and str

##### Creating Stirng Values

##### Simple Inspection

##### Appending and Inserting Text

##### Removing and Replacing Text

##### Conventions for Searching and Iterating

##### Conventions for Searching Text

##### Patterns for Searching Text

##### Searching and Replacing

##### Iterating over Text

##### Trimming

##### Case Conversion for String

##### Parsing Other Types from String

##### Converting Other types to String

##### Borrowing as Other Text-Like Types

##### Acessing Text as UTF-8

##### Producing Text from UTF-8 Data

##### Putting Off Allocation

##### Strings as Generic Collections

#### Formatting Values

##### Formatting Text Values

##### Formatting Numbers

##### Formatting Other Types

##### Formatting Values for Debugging

##### Formatting Pointers for Debugging

##### Referring to Arguments by Index or Name

##### Dynamic Widths and Precisions

##### Formatting Your Own Types

##### Using the Formatting Language in Your Own Code

#### Regular Expressions

##### Basic Regex Use

##### Building Regex Values Lazily

#### Normalization

##### Normalization Forms

##### The unicode-normilization Crate

### Input and Output

#### Readers and Writers

##### Readers

##### Buffered Readers

##### Reading Lines

##### Collecting Lines

##### Writers

##### Files

##### Seeking

##### Other Reader and Writer Types

##### Binary Data, Compression, and Serialization

#### Files and Directories

##### OsStr and Path

##### Path and PathBuf Methods

##### Filesystem Access Functions

##### Reading Directories

##### Platform-Specific Features

#### Networking

### Concurrency

#### Fork-Join Parallelism

##### Spawn and join

##### Error Handling Across Threads

##### Sharing Immutable Data Across Threads

##### Rayon

##### Revisiting the Mandelbrot Set

#### Channels

##### Sending Values

##### Receiving Values

##### Running the Pipeline

##### Channel Features and Performance

##### Thread Safety: Send and Sync

##### Piping Almost Any Iterator to a Channel

##### Beyond Pipelines

#### Shared Mutable State

##### What is a Mutex?

##### `Mutex<T>`

##### mut and Mutex

##### Why Mutexes Are Not Always a Good Idea

##### Deadlock

##### Poisoned Mutexes

##### Multiconsumer Channels Using Mutexes

##### Read/Write Locks (`RwLock<T>`)

##### Condition Variables (Condvar)

##### Atomics

##### Global Varialbes

#### What Hacking Concurrent Code in Ruse is Like

### Asynchronous Programming

#### From Synchronous to Asynchronous

##### Futures

##### Async Functions and Await Expressions

##### Calling Async Functions from Synchronous Code

##### Spawning Async Tasks

##### Async Blocks

##### Building Async Functions from Async Blocks

##### Spawning Async Tasks on a Thread Pool

##### But Does Your Future Implement Send?

##### Long Running Computations: yield_now and spawn_blocking

##### Comparing Asynchronous Designs

##### A Real Asynchronous HTTP Client

#### An Asynchronous Client and Server

##### Error and Result Types

##### The Protocol

##### Taking User Input: Asynchronous Streams

##### Sending Packets

##### Receiving Packets: More Asynchronous Streams

##### The Client's Main Functions

##### The Server's Main Functions

##### Handling Chat Connections: Async Mutexes

##### The Group Table: Synchronous Mutexes

##### Chat Groups: tokio's Broadcast Channels

#### Primitive Features and Executors: When Is a Future Worth Polling Again?

##### Involking Wakers: `spawn_blocking`

##### Implementing `block_on`

#### Pinning

##### The Two Life Stages of a Future

##### Pinned Pointers

##### The Unpin Trait

#### When Is Asynchronous Code Helpful?

### Macros

#### Macros Basics

##### Basics of Macro Expansion

##### Unintended Consequences

##### Repetition

#### Built-in Macros

#### Debugging Macros

#### Building the json! Macro

##### Fragment Types

##### Recursion in Macros

##### Using Traits with Macros

##### Scoping and Hygiene

#### Avoiding Syntax Errors During Matching

#### Beyond macro_rules!

### Unsafe Code

#### Unsafe from What?

#### Unsafe Blocks

#### Example: An Efficient ASCII String Type

#### Unsafe Functions

#### Unsafe Block or Unsafe Function?

#### Undefined Behavior

#### Unsafe Traits

#### Raw Pointers

##### Dereferencing Raw Pointers Safely

##### Example: RefWithFlag

##### Nullable Pointers

##### Type Sizes and Alignments

##### Pointer Arithmetic

##### Moving into and out of Memory

##### Example: GapBuffer

##### Panic Safety in Unsafe Code

#### Reinterpreting Memory with Unions

#### Matching Unions

#### Borrowing Unions

### Foreign Functions

#### Finding Common Data Representations

#### Declaring Foreign Functions and Variables

#### Using Functions from Libraries

#### A Raw Interface to libgit2

#### A Safe Interface to libgit2

#### Conclusion
