# Passing Values Into Functions:

```python nums
def my_function(something):
	# Do this with something
	# Then do this
	# Finally do this

my_function(something) # Valid
my_function(something_else) # Valid

my_function() # Error
```

Argument must be given, if a function that expects an argument is called without supplying an argument, this will result in a type error.

![](Pictures/Functions%20with%20Inputs%20Paramater%20and%20Argument.png)
# Functions With More Than One Argument:
## Positional Arguments

```python nums
def greet_with(name, location):
    print(f"Hello {name}.")
    print(f"What is it like in {location}?")

greet_with("Brad", "Cape Town") 

# Hello Brad.
# What is it like in Cape Town?


greet_with("Cape Town", "Brad") 

# Hello Cape Town.
# What is it like in Brad?
```

The order in which arguments are given in this example will affect how the arguments are handled inside the function.
## Keyword Arguments

```python nums
def greet_with(name, location):
    print(f"Hello {name}.")
    print(f"What is it like in {location}?")

greet_with(name = "Brad", location = "Cape Town")

# Hello Brad.
# What is it like in Cape Town?

greet_with(location = "Cape Town", name = "Brad")

# Hello Brad.
# What is it like in Cape Town?
```

We can ensure that arguments are passed to the correct variables inside the function by specifying which variable the argument should be passed to in our function call. This way no matter the order of our function arguments we can be sure that they will be supplied to the correct variables inside the function and as a result produce a predictable output.