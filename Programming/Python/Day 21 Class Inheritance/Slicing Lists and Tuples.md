# Introduction

We can use the `:` symbol to `slice` lists and tuples by specifying a position to begin the slice and a position to end the slice.

```python 
piano_keys = ["a", "b", "c", "d", "e", "f", "g"]

print(piano_keys[2:5])
# ['c', 'd', 'e']
```
# Slice Increments

You can append your slice syntax with another `:` symbol to specify a step size for what is returned by the slice.

```python
piano_keys = ["a", "b", "c", "d", "e", "f", "g"]

print(piano_keys[2:5:2])
# ['c', 'e']
```

You can also leave the beginning and end empty to slice the entire list by that step size:

```python
piano_keys = ["a", "b", "c", "d", "e", "f", "g"]

print(piano_keys[::2])
# ["a", "c", "e", "g"]
```
# Reversing a List using Slices

Specifying a negative step size will return the list in a reverse order.

```python
piano_keys = ["a", "b", "c", "d", "e", "f", "g"]

print(piano_keys[::-1])
# ["g", "f", "e", "d", "c", "b", "a"]
```