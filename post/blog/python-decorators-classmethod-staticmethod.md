---
authors:
  - Matt2ology
categories:
  - blog
  - python
date: 2025-01-29T09:51:26-08:00
draft: true
notes: blog
related-notes: 
tags: 
title: Python Decorators `classmethod` and `staticmethod`
---

## TL;DR (Too Long; Didn't Read)

Use `@classmethod` when you need to access or modify class variables.

Use `@staticmethod` when you need a function inside a class but don't need class or instance data. Allows you to write a function without using `self` or `cls`.

| Decorator       | Receives `cls`? | Receives `self`? | Can modify class variables? | Can modify instance variables? |
| --------------- | :-------------: | :--------------: | :-------------------------: | :----------------------------: |
| `@classmethod`  |      ✅ Yes      |       ❌ No       |            ✅ Yes            |              ❌ No              |
| `@staticmethod` |      ❌ No       |       ❌ No       |            ❌ No             |              ❌ No              |

## Decorators `@classmethod` and `@staticmethod`

<!-- [Propose edits or changes on GitHub](link to GitHub repo of file) -->

<!-- Propose edits or changes on GitHub -->

In Python, `@classmethod` and `@staticmethod` are **decorators** used to define methods inside a class. They change how the method behaves and how it interacts with the class and its instances.

```python
class Utility:
    counter = 0  # Class variable

    @classmethod
    def increment_counter(cls):
        cls.counter += 1  # Modify class variable
        print(f"Counter updated: {cls.counter}")

    @staticmethod
    def greet(name):
        print(f"Hello, {name}!")

def main():
    Utility.greet("Alice")  # Calls static method (doesn't use class state)
    Utility.increment_counter()  # Calls class method (modifies class state)

if __name__ == "__main__":
    main()  # Runs only if the script is executed directly
```

### `@classmethod` 

- A class method receives **the class itself** (`cls`) as the first argument.
- It can access and modify **class variables** but **not instance variables**.
- It is used when a method needs to work at the **class level**, rather than on specific instances.

**Example**

```python
class MyClass:
    class_variable = 0  # A class attribute

    @classmethod
    def set_class_variable(cls, value):
        cls.class_variable = value  # Modifies the class attribute

def main():
    MyClass.set_class_variable(10)  # Calls class method
    print(MyClass.class_variable)  # Output: 10

if __name__ == "__main__":
    main()
```

### `@staticmethod`

- A static method **does not receive** the class (`cls`) or instance (`self`) as arguments.
- It behaves like a **regular function** inside the class but is **logically related** to the class.
- It **cannot** modify class or instance variables.

**Example**

```python
class MathOperations:
    @staticmethod
    def add(a, b):
        return a + b  # Simple operation, no class or instance data needed

def main():
    result = MathOperations.add(5, 3)  # Calls static method
    print(result)  # Output: 8

if __name__ == "__main__":
    main()
```

## Related blogs

<!-- [Related blog post]({{< ref "/post/blog/path_to_file.md" >}}) -->

-
