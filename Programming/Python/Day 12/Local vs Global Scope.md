# Functions:

```python nums
enemies = 1

def increase_enemies():
	enemies = 2
	print(f"enemies inside function: {enemies}") # 2

increase_enemies()
print(f"enemies outside function: {enemies}") # 1
```

Python can't modify global variables from within functions, in the above example it will create a new variable within the scope of the function with the same name and print that instead.

```python nums
foo = 10

def bar():
    print(foo)

bar() # 10
```

You are however able to access variables within the scope of the function, in this case we can print the contents of the global variable.
# Block Scope

There is no block scope in Python

```python nums
if True:
    foo = 10

print(foo) # 10
```
# Modifying a Global Variable

```python nums
bar = 1

def foo():
    global bar
    bar = 2
    print(bar)

print(bar)
foo()
print(bar)
```

The `global` keyword must be used followed by the variable name on it's own line when you intend to modify a global variable within a function in python.