---
authors:
  - Matt2ology
categories:
  - blog
  - code-challenge
date: 2025-02-02T22:12:48-08:00
draft: true
notes: blog
related-notes:
  - "[[advent-of-code-2024]]"
tags:
  - advent-of-code-2024
title: Advent of Code 2024 Day 01
---

## [Day 1: Historian Hysteria](https://adventofcode.com/2024/day/1)

[Advent of Code 2024]({{< ref "advent-of-code-2024.md" >}})

### The problem

> By holding the two lists up side by side, it quickly becomes clear that the lists aren't very similar. Maybe the lists are only off by a small amount! To find out, pair up the numbers and measure how far apart they are. Pair up the smallest number in the left list with the smallest number in the right list, then the second-smallest left number with the second-smallest right number, and so on.
>
> For example, if you pair up a `3` from the left list with a `7` from the right list, the distance apart is `4`; if you pair up a `9` with a `3`, the distance apart is `6`.

Example input

```text
3   4
4   3
2   5
1   3
3   9
3   3
```

Example input when processed

```text
1   3 delta of 2
2   3 delta of 1
3   3 delta of 0
3   4 delta of 1
3   5 delta of 2
4   9 delta of 5
=====
sum of 11
```

### Decomposition of Problem: Divide-and-conquer / Stepwise Refinement

- **Sequence**: First, pair up numbers from the left and right list in order (smallest to smallest, second smallest to second smallest, etc.).
- **Selection**: Select the smallest elements from each list if they aren't already sorted.
- **Iteration**: Use a loop to go through the lists and perform the comparison for each pair, calculating the differences.

## Research Log

- [python read from file](https://www.w3schools.com/python/python_file_open.asp)
