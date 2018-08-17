---
layout: post
title: "Mypy - Optional static typing for Python"
description: "Introduction to type annotations and mypy"
date: 2018-21-03
tags: jekyll
comments: true
---

`mypy` is an experimental static type checker for Python. As Python is a dynamically typed language, mypy aims to combine the benefits of dynamic typing and static typing.

In other words, mypy is like a linter that scans your code and prints out errors if there are any type conflicts.

## Role of PEP-484
PEP-484 introduced the standard of type annotations (type hints) in Python. This standard came into existence from Python 3.5. This proposal adds syntax to Python for annotating the types of variables including class and instance variables.

If you’re using Python 3.5 or greater, you can write function definitions as shown below

```
def func(argv: Optional[Sequence[str]]) -> None: ...
```

In the above snippet, the term after `:` represents the type of the parameter and the term after -> represents the return type of the function.

With the addition of PEP-484, Python 3.5 gained two things:

1. A standard for describing types
2. A syntax support for annotating function arguments and the return values.

Now that we know about type annotations, but what exactly is type checking?

Inspection of code to enforce that arguments and assignments match their declared types is known as *type checking*.

Python 3.5 introduced type annotations but it didn’t come with built-in type checking. Core developers left the role to be filled by third party tools.

There are handful of tools that perform PEP-484 compatible type checking and `mypy` is one of them.

Annotation syntax for function declarations in Python 3 is as shown below

```
def plus(num1: int, num2: int) -> int:
    return num1 + num2
```

To check Python 3 code against `mypy`, run the command `mypy program.py`.

Since type annotations were introduced in Python 3, for code that needs to be Python 2.7 compatible, function type annotations are given in comments as shown below. This syntax is also valid in Python 3 mode.

```
def plus(num1, num2):
    # type: (int, int) -> int
    return num1 + num2
```

To check Python 2 code against `mypy`, run mypy in Python 2 mode using the *— py2* option.



## Using Mypy

When a script is run with a standard Python interpreter, the type annotations are treated primarily as comments. As `mypy` is a static analyzer, it does not cause any overhead when running the program.

Let’s take a look at a simple example:

```
def function(number: int, name: str) -> None:
	print("%s entered %s" % (name, number))
```

Above function takes in two parameters one of the type `int` and other of type `str`.

If we call the function as `function(4, “John”)` and run `mypy`, issuing the command `mypy program.py`, we get no errors or warnings. So the provided type annotations are correct.

However if we call the above function as `function(“4", “John”)` and run `mypy`, it throws an error saying error: Argument 1 to “function” has incompatible type “str”; expected “int”

Using `mypy`, common code bugs can be found and it checks the code for proper arguments and return types.

Remember that a function without a type annotation is considered dynamically typed.
