---
authors: Brian Ward
categories:
  - reference
date: 2025-01-21
draft: true

sources: kindle
media: books
notes: reference
tags: readwise, reference/books
title: Reference - Brian Ward - How Linux Works
---

## How Linux Works (Highlights)

![rw-book-cover](https://m.media-amazon.com/images/I/81K+2pqDU-L._SY160.jpg)

Source published date: None

## Highlights

### Location 926

> The first edition included historical information that I removed later to improve focus. If you’re interested in Linux and how it relates to the history of Unix, pick up Peter H. Salus’s The Daemon, the Gnu, and the Penguin (Reed Media Services, 2008).
> \- [(Location 926)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=926)

**Initial thought or note on:** [(Location 926)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=926)
The recommended book, [The Daemon, the Gnu, and the Penguin](https://www.amazon.com/Daemon-Gnu-Penguin-Peter-Salus-ebook/dp/B004ZH3OZW/ref=tmm_kin_swatch_0?_encoding=UTF8&qid=&sr=), covers how the software we used evolved over time.

### Location 939

> The most effective way to understand how an operating system works is through abstraction—a fancy way of saying that you can ignore most of the details that make up a piece that you’re trying to understand, and concentrate instead on its basic purpose and operation.
> \- [(Location 939)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=939)

**Initial thought or note on:** [(Location 939)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=939)
Can't see the forest for the trees... All too often one may get fixated on a particular component where in it of itself is a whole "process" and is distracted by this instead of understanding "just-enough" to continue the flow of understanding the system as a whole.

### Location 969

> The kernel is software residing in memory that tells the CPU where to look for its next task. Acting as a mediator, the kernel manages the hardware (especially main memory) and is the primary interface between the hardware and any running program.
> \- [(Location 969)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=969)

**Initial thought or note on:** [(Location 969)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=969)
The core of the operating system

### Location 978

> Code running in kernel mode has unrestricted access to the processor and main memory. This is a powerful but dangerous privilege that allows the kernel to easily corrupt and crash the entire system. The memory area that only the kernel can access is called kernel space.
> \- [(Location 978)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=978)

**Initial thought or note on:** [(Location 978)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=978)
Because this is the "core" of the operating system the kernel has full access to all resources available.

### Location 980

> User mode, in comparison, restricts access to a (usually quite small) subset of memory and safe CPU operations. User space refers to the parts of main memory that the user processes can access.
> \- [(Location 980)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=980)

**Initial thought or note on:** [(Location 980)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=980)
Adhering to the "principle of least privilege" a user has accesses to a subset of memory and is allowed to execute safe CPU operations. If a user needs to have full access they may go into "Super User" mode. This way "critical" operations of the system and other elements are not affected by errors of the user.

### Location 996

> A CPU is just an operator on memory; it reads its instructions and data from the memory and writes data back out to the memory.
> \- [(Location 996)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=996)

### Location 997

> the term state in reference to memory, processes, the kernel, and other parts of a computer system. Strictly speaking, a state is a particular arrangement of bits. For example, if you have four bits in your memory, 0110, 0001, and 1011 represent three different states.
> \- [(Location 997)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=997)

**Initial thought or note on:** [(Location 997)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=997)
Process States: While a process executes, over time it changes state

### Location 1005

> it’s common to refer to the state in abstract terms rather than to the actual bits, the term image refers to a particular physical arrangement of bits.
> \- [(Location 1005)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=1005)

### Location 1008

> Nearly everything that the kernel does revolves around main memory. One of the kernel’s tasks is to split memory into many subdivisions, and it must maintain certain state information about those subdivisions at all times. Each process gets its own share of memory, and the kernel must ensure that each process keeps to its share.
> \- [(Location 1008)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=1008)

### Location 1010

> The kernel is in charge of managing tasks in four general system areas: Processes The kernel is responsible for determining which processes are allowed to use the CPU. Memory The kernel needs to keep track of all memory—what is currently allocated to a particular process, what might be shared between processes, and what is free. Device drivers The kernel acts as an interface between hardware (such as a disk) and processes. It’s usually the kernel’s job to operate the hardware. System calls and support Processes normally use system calls to communicate with the kernel.
> \- [(Location 1010)](https://readwise.io/to_kindle?action=open&asin=B07X7S1JMB&location=1010)
