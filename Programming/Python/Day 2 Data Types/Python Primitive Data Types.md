# Introduction

- Strings - Array of Characters
- Integers - Whole Numbers
- Floats - Floating Point Numbers
- Booleans - True or False Conditions

# Strings

Because a string is an array of characters we can use square brackets `[]` to access individual characters in the string.

```python
print("Hello"[0]) # H
```

**Note:** Python also operates with 0 being the first index in an array, not 1.

This method of pulling out a single element of a string is called **subscripting**.

Negative indexes can also be used in Python, meaning that to get the last character of a string we can use -1 as the index.

```python
print("Hello"[-1]) # o
```

# Integers

Underscores can be used inside of integers to simplify reading big numbers, these have no effect on the actual way that the number is interpreted by python, it will simply remove the underscores.

```python
print(123_456_789) # 123456789
```

# Floats

 ```python
 print(3.14159)
 ```

# Boolean

```python
print(True) # True
print(False) # False
```