# Introduction

`print()` is the keyword to print information to the console.  

We can print the classic "Hello world!" text with the following:

```python nums
print("Hello world!")
```

Quotation marks `"` are required to print text, indicating to the function that the information passed into it is a string.

# String Manipulation

## New Line `\n`

The escape code `\n` can be used to print text on new lines without the need for adding a new print statement on every line.

```python
print("Hello world!\nHello world!\nHello world!")
```

## Concatenation `+`

We can use the concatenation operator `+` between strings to concatenate them together in our output statement.

```python
print("Hello"+"Angela")   # HelloAngela
```

Note that there will be no space in between these two strings.

### Note on Spaces:

When writing code in Python the placement of spaces is very important.  

For example: The following would cause an indentation error:

```python
 print("Hello"+"Angela")   # HelloAngela
^ space present = error

print("Hello"+"Angela")   # HelloAngela
^ no space present = no error
```

#### Note on Errors:

The errors produced in the editor such as red highlights or squiggly lines under the text are produced by your editor and it's important to understand that this will differ from editor to editor. It's also important to see the error produced by the compiler after running the program as that will be consistent regardless of the editor that you use.

# The `input()` Function

The `input()` function can be used to prompt the user to input inside of the console.

```python
input("What is your name?")
```

Note that the string to output to the user is included in the input function and can be entered between brackets.

Now when we run the program the string will be presented to the user and the program will wait for user input before continuing.

![](Pictures/Printing%20to%20the%20Console%20-%20Waiting%20for%20User%20Input.png)

In the above screenshot, at the top right hand corner, you can see that there is now a stop button in the place of where the play button was, this is because the program is still running while it waits for user input.

## Return

The `input()` function returns what is inputted by the user.

```python
print("Hello " + input("What is your name?"))
```

In this example the function call `input()` will need to be completed before `print()` can execute and so the output will be as follows:

```
What is your name?
# Input: Brad
Hello Brad
```

### Note on Comments:

To add comments to code in python you will need to place a `#` symbol at the start of your comment.