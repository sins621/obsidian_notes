# Listening for Key Presses

To manage input with the Turtle Library we can use the `Turtle.screen.onkey(fun,key)` method.

```python
def forward():
    fd(50) # forward

screen.onkey(forward, "space")
screen.listen()
```

The `listen()` function sets focus to the turtle window and enables it to listen for key press events.
# Functions as Inputs

Note that when functions are passed in as arguments to other functions the parenthesis `()`  are not required.

```python
def function_a(something):
	#Do this with something
	#Then do this
	#Finally do this

def function_b():
	#Do this

function_a(function_b)
```
# Higher Order Functions

```python
def add(n1,n2):
	return n1 + n2

def sub(n1,n2):
	return n1 - n2

def multiply(n1,n2):
	return n1 * n2

def divide(n1, n2):
	return n1 / n2

def calculator(n1, n2, func):
	return func(n1, n2)

result = calculator(2, 3, add)
print(result) # 5

result = calculator(3, 2, sub)
print(result) # 1
```

In this example, `calculator` is a **higher-order function** because it takes another function (like `add`, `sub`, `multiply`, or `divide`) as an argument and uses it to perform a specific operation. This makes `calculator` flexible, as it can “orchestrate” the behavior of multiple other functions by applying the passed function (`func`) to its two inputs (`n1` and `n2`).

By passing different functions to `calculator`, you’re able to achieve different results without needing to modify the `calculator` function itself.