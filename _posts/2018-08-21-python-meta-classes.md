---
layout: post
title: "Typing module in Python"
description: "Understanding Typing module in Python"
date: 2018-08-21
tags: python
comments: true
---

Declaring `int`, `str`, `float` variables is simple but declaring complex data types like List of tuples, List of dictionaries etc is cumbersome. This is where `typing` module comes to rescue.

The typing module in Python 3.6 contains many definitions that are useful in statically typed code.

Here’s how to use the typing module in Python 3:


```
from typing import Tuple, List, Dict

data: Tuple[int, str, List[int]] = (3, "Python" [1, 2, 3])
x: Dict[str, float]  = {'field': 2.0}
```

As generator function is also a function that returns an Iterable, here’s how to type annotate it :

```
from typing import Iterable
def f(n: int) -> Iterable[int]:
    i = 0
    while i < n:
        yield i
        i += 1
```

Below snippet uses the Union type which is used to specify that the address argument can either be a string or a list of strings and the type Optional is specified for values that could be None.

```
from typing import Union, Optional
def send_email(address: Union[str, List[str]],
               cc: Optional[List[str]
              ) -> bool: ...
```

Here’s how to type annotate Python 2 code using comments :

```
from typing import Tuple, List, Dict, Optional, Union, Iterable

data = (3, "Python" [1, 2, 3]) # type: Tuple[int, str, List[int]]
x = {'field': 2.0} # type: Dict[str, float]
def f(n: int):
    # type: (int) -> Iterable[int]
    i = 0
    while i < n:
        yield i
        i += 1
def send_email(address, # type: Union[str, List[str]],
               cc,      # type: Optional[List[str]
              ):
# type: (...) -> bool
...

```

## Using Type aliases

Type aliases can be defined by using simple variable assignments. It’s generally used when the type gets lengthier. In below exampleExampleType can be referenced at all places where the variable data is used.

```
ExampleType = Tuple[int, str, List[int]]
data: ExampleType = (3, "Python" [1, 2, 3])
```

##Creating your own types

In Python 3.5 a new function is introduced in typing called NewType. This allows you to create distinct types. The static type checker will treat the new type as if it were a subclass of the original type. You may still perform all int operations on a variable of type UserId, but the result will always be of type `int`.

```
from typing import NewType

UserId = NewType('UserId', int)
some_id = UserId(524313)
```

One of the best use cases of mypy is that it helps in self documenting code to an extent. Some of the large code bases can be tough to read. It’s difficult to tell what a function or a class accepts. Type hinting would help in adding clarity and readability to code.

Awesome folks at Dropbox built a Pycharm plugin that type checks and highlights the errors in the file.

For more information about mypy and typing I would recommend reading their official documentation. And for folks starting on type hinting their Python projects I would recommend reading this blog where Tim Abbott detailed how Zulip started with and implemented type hinting.
