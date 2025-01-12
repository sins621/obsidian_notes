# Introduction

Inheritance allows to create a new class which inherits attributes and methods from another class.

```python
class Animal:
    def __init__(self):
        print("Animal created")

class Fish(Animal):
    def __init__(self):
        super().__init__()
        print("Fish created")
```

The syntax to create a class which inherits from another class is to place the name of the class we are inheriting from inside of the parenthesis. `Fish` then becomes a *subclass* of `Animal`

`class Fish(Animal)`

Using `super().__init__()` in the `Fish` class calls the `__init__` method of `Animal`, ensuring any setup in the `Animal` class is applied to `Fish` as well. This allows for creating specialized versions of classes without repeating code.
# Expanding on the Super Class

![](Pictures/Class%20Inheritance%20-%20Fish%20Animal%20Example.png)

In this example when we initialize `Fish` we call `super()` with the `__init__()` method meaning that fish will now have the attribute `num_eyes` and we extend the functionality of `Animal`'s `breathe()` method by calling it inside of the sub class using `super()` and then adding more code.