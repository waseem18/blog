---
layout: post
title: "Python metaclasses - What, Why and How!"
description: "Understanding metaclasses in Python"
date: 2018-08-21
tags: jekyll
comments: true
---

*This blog post is WIP*

Everything in Python is an object. So Lists, Strings, Functions, Modules, Classes everything are objects. Wait, but what actually is an *object*?

Different programming languages define *object* in a different style. Talking about Python, *everything is an object* in the sense that it can be assigned to a variable or passed as an argument to a function. In short, anything that goes on the right hand side of the equation is an object.

## Classes as Objects

Classes are objects too in Python. As classes are objects, we can

* Assign a class to a variable
* Add attributes to it
* Can pass it as a function parameter

```
class DummyClass(object):
  pass

# Function func takes class as an argument
def func(DummyClass):
  pass

# Assigining class to a variable
a = DummyClass

# Passing class as a parameter to a function
func(DummyClass)
```
