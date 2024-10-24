# Introduction

Functions can also be made to expect specific types as arguments when called.

# Checking Types

The `type()` function can be used to return the type of the data that is passed to it as an argument.

```python
print(type("Hello")) # <class 'str'>
print(type(123)) # <class 'int'>
print(type(1.1)) # <class 'float'>
print(type(True)) # <class 'bool'>
```

# Type Conversion

We can convert a string to an integer for example using the `int()` function.

```python
print(int("123") + int("456")) # 579
```

However it's still important to consider that some conversions are not possible and will produce compiler errors.

```python
print(int("abc")) # Value Error: Invalid Literal
```

Type conversions can be used for all major types.

```Python
int()
float()
str()
bool()
```

