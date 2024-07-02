---
title: Non-SNS
layout: default
parent: Python 
grand_parent: Coding Practices
---
# Non-SNS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Dunner variables

>FYI, there are a few dunner methods/ variables <br/>
> You can find them via `print(dir())` <br/>
> These are the listed ones: <br/>
> `__annotations__, __builtins__, __cached__, __doc__, __file__, __loader__, __name__, __package__, __spec__`
{:.note}

## Using `if __name__ = "__main__"`

- Running python file directly 
```python
print(__name__) # returns __main__

# Explained: When running python file directly, __name__ is set to main
```

- Running python file via import <br/>

fileA
```python
print(__name__) # returns __main__

# Explained: When running python file directly, __name__ is set to main
```

fileB
```python
import fileA # returns fileA

#Explained: Since fileB imported fileA, meaning fileA was ran once through fileB
```

- Running python file via import methods <br/>

fileA
```python
def do_something():
    print('doing something')

do_something()

# Explained: When running python file directly, __name__ is set to main
```

fileB
```python
from fileA import do_something # returns 1st print statement

do_something() # This returns 2 print statments

#Explained: Since fileB imported fileA, meaning fileA was ran once through fileB
```