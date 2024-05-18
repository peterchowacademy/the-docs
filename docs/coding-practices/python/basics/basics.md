---
title: Basics
layout: default
parent: Python 
grand_parent: Coding Practices
---

# Python basics
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Dunder Methods 
## 5 useful dunder methods ```__eq__``` ```__format__``` ```__or__``` ```__repr__``` ```__getitem__``` 
{: .fs-6 .fw-300 }

We will use the follow Fruit class as basis for all the following examples
{:.warning}

Please refer to [this](https://www.youtube.com/watch?v=y1ZWQQEe5PM) youtube video

```python 
class Fruit:
    # * forces name & grams to be manditory keyword arguments
    def __init__(self, *, name:str, grams:float) -> None: 
        self.name = name 
        self.grams = grams

def main() -> None:

if __name__ == '__main__':
    main()
```
Have fun and try to understand these 5 dunner methods and use it alongside `__init__` ~
{:.warning}

### Let's start with  ```__eq__``` (TLDR: using `__eq__` changes how `==` performs)

``` python
class Fruit:
    # * forces name & grams to be manditory keyword arguments
    def __init__(self, *, name:str, grams:float) -> None: 
        self.name = name #Assign both input value to the instance
        self.grams = grams

    ########################################## Showcasing __eq__ ##########################################
    # Comparing instances from instances (it's clear now that Self has to be another class of Fruit)
    def __eq__(self, other:Self) -> bool:
        #This compares both name and grams as a dictionary!
        return  self.__dict__ == other.__dict__ 
    ########################################## End of showcasing __eq__ ###################################

# Let's instantiate a 2 instances from this object 
def main() -> None:
    f1: Fruit = Fruit(name='Apple', grams=100) #f1 and f2 are alias, that has type Fruit
    f2: Fruit = Fruit(name='Orange', grams=150)
    f3: Fruit = Fruit(name='Apple', grams=100)

    #Let's check to see if f1 and f2 are equal
    print(f1 == f2) # Returns false due to different memory addresses (not their values) 
    print(f1 == f3) # Before implementing __eq__, returns false (since diff mem address)
                    # After __eq__, returns true (since name and grams are compared in a dict)

if __name__ == '__main__':
    main()

```
### Format speicifier: ```__format__``` (TLDR: variable:kg -> triggers `__format__`)

```python 
class Fruit:
    # * forces name & grams to be manditory keyword arguments
    def __init__(self, *, name:str, grams:float) -> None: 
        self.name = name 
        self.grams = grams
    ########################################## Showcasing __format__ ##########################################
    # Comparing instances from instances (it's clear now that Self has to be another class of Fruit)
    def __format__(self, format_spec:str) -> str:
        match format_spec:
            case 'kg':
                return f'{self.grams / 1000:.2f} kg' #formatted to 2 d.p
            case 'desc': # Description
                return f'{self.grams} of {self.name} !!'
            case _: #Raise value error to signal user 
                raise ValueError('Unknown format specifier...') 
    ########################################## End of showcasing __format__ ###################################
    

def main() -> None:
    apple: Fruit = Fruit(name='Apple', grams=2500)
    print(f'{apple:kg}') # This will trigger the format specifier, returns 2.50 kg

if __name__ == '__main__':
    main()
```

### Or dunner method ```__or__``` (TLDR: )

Quick demo of the union opertor in action, the vertical bar symbol <a href="https://wumbo.net/symbols/vertical-bar/"> click me </a> <br/>
The demo can also be shown in the following example
```python 
class Fruit:
    # * forces name & grams to be manditory keyword arguments
    def __init__(self, *, name:str, grams:float) -> None: 
        self.name = name 
        self.grams = grams

def main() -> None:
    d1: dict = {1:'a', 2:'b'}
    d2: dict = {3:'c', 4:'d'}

    s1:set = {1,2}
    s2:set = {3,4}
    print(d1 | d2) # | is the union operator (works w/ sets and dictionary) #get back all the key and value pairs

    print(s1 | s2) # get back all the values

if __name__ == '__main__':
    main()
```

Back to our example for ``` __or__``` use:

```python
class Fruit:
    # * forces name & grams to be manditory keyword arguments
    def __init__(self, *, name:str, grams:float) -> None: 
        self.name = name 
        self.grams = grams
    ########################################## Showcasing __or__ ##########################################
    # Comparing instances from instances (it's clear now that Self has to be another class of Fruit)
    def __or__(self, other:Self) -> str:
        new_name:str = f'{self.name} & {other.name}'
        new_grams:float = self.grams + other.grams
        return Fruit(name=new_name, grams=new_grams) #setting new name and new grams
    ########################################## End of showcasing __or__ ###################################
    

def main() -> None:
    apple: Fruit = Fruit(name='Apple', grams=2500)
    orange: Fruit = Fruit(name='Orange', grams=2500)
    banana: Fruit = Fruit(name='Banana', grams=2500)

    combined:Fruit = apple|orange # without __or__ this will throw an error since this logic was not implemented
                                

if __name__ == '__main__':
    main()
```