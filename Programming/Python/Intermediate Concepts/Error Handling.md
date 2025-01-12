# Introduction

When we write code that produces an error it generally stops the program, for instance here's a few lines that create a **Tkinter** Window:

```python
from tkinter import *

window = Tk()

window.mainloop()
```

What you expect is for a window to be created and stay open such as can be seen in the following image:

![](Pictures/Try%20Catch%20Except%20Finally%20-%20Window.png)

If an error occurs before reaching the `mainloop()` method however then our Window will not stay open, for example if we were to attempt to access a file that doesn't exist:

![](Pictures/Try%20Catch%20Except%20Finally%20-%20Error.png)

We can see here that we have created a `FileNotFoundError` and our window does not stay open.

We can however  *catch* this error, handle it and then proceed.
# Try Except Else Finally

We can use the `try` keyword to attempt lines of code and then use the `except` keyword to execute lines of code in the event that the code in the `try` block produces an error.

![](Pictures/Error%20Handling%20-%20Try%20Except.png)

Here our window stays open because in the event that the file does indeed not exist, we will then use the `"w"` argument to *write* a new file which we can then assign to the `file` variable.

![](Pictures/Error%20Handling%20-%20File.png)

And here we can see that the file has been created.

Once we are sure that the file will indeed exist we can then read from the existing file using the `else` argument. This argument ==will only execute if the== `try` ==was successful==.

```python
try:
    file = open("non_existent_file.txt") 
except:
    file = open("non_existent_file.txt", "w")
else:
    contents = file.read()
    print(contents)
```

I've gone ahead and put something in the file and below you can see the successful printing of the file's contents:

![](Pictures/Error%20Handling%20-%20Something.png)

Now we want to be sure that we are always closing the file to free up resources and we will need to do this regardless of whether or not we read or create the file in this instance. For this we can use the `finally` keyword, this code will execute after all other operations have taken place.

```python
try:
    file = open("non_existent_file.txt") 
except:
    file = open("non_existent_file.txt", "w")
else:
    contents = file.read()
    print(contents)
finally:
    file.close()
```
# Catching Specific Errors:

The important thing to note is in this example our `except` block will execute on **any** errors that may occur, for example say we create a `KeyError` by attempting to access a key that doesn't exist in a dictionary.

![](Pictures/Error%20Handling%20-%20No%20Key%20Error.png)

We can see that in this case we trigger the exception but no `KeyError` is presented. This is because the exception will be triggered if any error is produced by the code within the `try` block. We will instead need to specify which error we are handling.

```python
try:
    file = open("non_existent_file.txt") 
    dictionary = {"key":"value"}
    print(dictionary["wrong_key"])
except FileNotFoundError:
    file = open("non_existent_file.txt", "w")
    print("Hit exception")
```

Now, running the code above:

![](Pictures/Error%20Handling%20-%20KeyError.png)

Now the error is presented to us, we can also handle the `KeyError`:

```python
try:
    file = open("non_existent_file.txt") 
    dictionary = {"key":"value"}
    print(dictionary["wrong_key"])
except FileNotFoundError:
    file = open("non_existent_file.txt", "w")
    print("File Not Found Error")
except KeyError:
    print("Key Error")
```

![](Pictures/Error%20Handling%20-%20Handled%20Key%20Error.png)

Now the code block under the exception for the `KeyError` is executed. We can still retain the usefulness of errors by capturing the error messages into variables with the following:

```python
try:
    dictionary = {"key": "value"}
    print(dictionary["wrong_key"])
except KeyError as error_message:
    print(f"Can't access {error_message}, not present in dictionary.")
```

![](Pictures/Error%20Handling%20-%20Error%20Message%20Saved.png)

Here we can see we have captured the name of the key we are trying to access and used it in our own error message, the important thing to note however is that our window will now still stay open even though we have produced and reported this error.
# Raising Our Own Exceptions

We can create our own errors by using the `raise` keyword, have a look at the following code:

```python
height = float(input("Height: "))
weight = int(input("Weight: "))

bmi = weight / height ** 2
print(bmi)
```

As long as the user enters numbers this could wouldn't generate any errors but let's say we wanted to raise an error if the user enters an unrealistic height. For instance the tallest human was 2.5 meters, there shouldn't ever be a human taller than 3 meters:

```python
if height >= 3:
    raise ValueError("You have entered an unrealistic height.")
```

By adding this line and entering a value 3 and above we can now see a value error with our own text being shown:

![](Pictures/Error%20Handling%20-%20Raised%20Exception.png)

