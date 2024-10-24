# Introduction

Say we want to store the information of the `input()` function, we can store user input inside a **variable**. 

```python
name = input("What is your name?")
```

Now that we've stored the user input inside of the `name` variable we can print that back to the console using the `print()` function with the variable as an **argument**.

```python nums
name = input("What is your name?")
# Input: Brad
print(name)
# Output: Brad
```

## Note: The `len()` Function

The `len()` function can be used to return the length of a string that is passed to it.

```python
len("Brad") # 4
```

# Example: Storing and Printing the Length of a String

```python nums
username = input("What is your name?")
length = len(username)
print(length)
```

# Variable Naming

Be sure to give variables descriptive names so that you can always follow what the code is doing regardless of how long it has been since you have worked on it.

```python nums
u = "Angela"
l = len(n)
print(l)
```

This is an example of bad variable naming, while it's simple to infer what these variables are storing from this small snippet it will be a lot more difficult to follow once you have a code base of thousands of lines.

Here's an example of good variable naming conventions:
```python nums
user_name = "Angela"
length = len(user_name)
print(length)
```

Note that the underscore character can be used in the place of a space inside variable names, spaces will cause compiler errors if you attempt to use them inside of your variable names.

It's also important to be cognizant of **keywords** and not to use keywords such as "input" from the `input()` function, while this may compile without errors, it's likely to cause confusion somewhere down the line.'

