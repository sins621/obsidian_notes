# Declaring a Dictionary with Functions

```python
def add(n1, n2):
    print(f"{n1} + {n2} = {n1+n2}")
    return n1 + n2


def subtract(n1, n2):
    print(f"{n1} - {n2} = {n1-n2}")
    return n1 - n2


def multiply(n1, n2):
    print(f"{n1} * {n2} = {n1*n2}")
    return n1 * n2


def divide(n1, n2):
    print(f"{n1} / {n2} = {n1/n2}")
    return n1 / n2


calculator = {
    "+": add,
    "-": subtract,
    "*": multiply,
    "/": divide,
}
```

Functions can be stored within dictionaries to be called later (pretty cool)
# Calling a Dictionary with Functions

```python
print(calculator["+"](5,10) 
# 5 + 10 = 15
# 15
```