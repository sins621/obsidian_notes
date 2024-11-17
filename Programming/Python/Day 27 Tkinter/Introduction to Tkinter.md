# Introduction

Tkinter is a python library built to create simple GUI programs.

To use Tkinter you will need to install the `tk` python pacakage. You can do so in your virtual environment by running `pip install tk`

The first step to a Tkinter program is to create the window for our GUI:

```python
import tkinter

window = tkinter.Tk()
```

Running this however won't display anything because the window will close when the program is no longer running. The keep the window open, or create a circumstance where the program does not immediately, we can use the following command:

```python
window.mainloop()
```

We can then provide a tile for our window and minimum width and height settings:

```python
window.title("My First GUI Program")
window.minsize(width=500, height=300)
```

Now we will have a window that looks like this:

![](Pictures/Introduction%20to%20Tkinter%20-%20Example%20Window.png)

# Labels

If we want to display text inside of our GUI we can create a label:

```python
my_lable = tkinter.Label(text="I am a label", font=("Arial", 24))
```

However, if we run the program now we will not see any text, we first need to call the `pack()` method which handles placing our label inside of our GUI:

```python
my_lable.pack(expand=True)
```

We should now have the following:

![](Pictures/Introduction%20to%20Tkinter%20-%20Label%20Example.png)

Other arguments and more information for the `pack()` method can be found [here](https://www.tutorialspoint.com/python/tk_pack.htm).
# Buttons

We can create intractable buttons for our GUI by creating `Button()` objects:

```python
import tkinter as tk

window = tk.Tk()

button = (text="My button")
```

![](Pictures/Introduction%20to%20Tkinter%20-%20Button.png)

We can then assign a function to this button using the `command` argument specifying the name of our function. Say we have the label from earlier and we would like to update it's text when we press the button:

```python
import tkinter as tk

window = tk.Tk()

label = tk.Label(text="I am a label", font=("Arial", 24, "normal"))
label.pack()

def button_clicked():
    label.config(text="Changed, Text")

button = tk.Button(text="Click me", command=button_clicked)
button.pack()

window.mainloop()
```

![](Pictures/Introduction%20to%20Tkinter%20-%20Prior%20to%20Clicking.png)

After we click on the button.

![](Pictures/Introduction%20to%20Tkinter%20-%20Button%20Clicked.png)

We can now see that the text has changed.
# Entry

We can also create a text input box by creating an `Entry()` object:

```python
input = tk.Entry(width=10)
input.pack()
```

![](Pictures/Introduction%20to%20Tkinter%20-%20Entry.png)

We can for example use this entry to write text to update our label:

```python
def button_clicked():
    text = input.get()
    label.config(text=text)

button = tk.Button(text="Click me", command=button_clicked)
button.pack()

input = tk.Entry(width=10)
input.pack()
```

By using the `.get()` method we can access a string of text inside the text box.

![](Pictures/Introduction%20to%20Tkinter%20-%20Button%20Text%20Entry.png)

We can see that the label text is updated when clicking on the button.
# Other Widgets:

![](Pictures/Introduction%20to%20Tkinter%20-%20Other%20Widgets.png)

```python
from tkinter import *

#Creating a new window and configurations
window = Tk()
window.title("Widget Examples")
window.minsize(width=500, height=500)

#Labels
label = Label(text="This is old text")
label.config(text="This is new text")
label.pack()

#Buttons
def action():
    print("Do something")

#calls action() when pressed
button = Button(text="Click Me", command=action)
button.pack()

#Entries
entry = Entry(width=30)
#Add some text to begin with
entry.insert(END, string="Some text to begin with.")
#Gets text in entry
print(entry.get())
entry.pack()

#Text
text = Text(height=5, width=30)
#Puts cursor in textbox.
text.focus()
#Adds some text to begin with.
text.insert(END, "Example of multi-line text entry.")
#Get's current value in textbox at line 1, character 0
print(text.get("1.0", END))
text.pack()

#Spinbox
def spinbox_used():
    #gets the current value in spinbox.
    print(spinbox.get())
spinbox = Spinbox(from_=0, to=10, width=5, command=spinbox_used)
spinbox.pack()

#Scale
#Called with current scale value.
def scale_used(value):
    print(value)
scale = Scale(from_=0, to=100, command=scale_used)
scale.pack()

#Checkbutton
def checkbutton_used():
    #Prints 1 if On button checked, otherwise 0.
    print(checked_state.get())
#variable to hold on to checked state, 0 is off, 1 is on.
checked_state = IntVar()
checkbutton = Checkbutton(text="Is On?", variable=checked_state, command=checkbutton_used)
checked_state.get()
checkbutton.pack()

#Radiobutton
def radio_used():
    print(radio_state.get())
#Variable to hold on to which radio button value is checked.
radio_state = IntVar()
radiobutton1 = Radiobutton(text="Option1", value=1, variable=radio_state, command=radio_used)
radiobutton2 = Radiobutton(text="Option2", value=2, variable=radio_state, command=radio_used)
radiobutton1.pack()
radiobutton2.pack()


#Listbox
def listbox_used(event):
    # Gets current selection from listbox
    print(listbox.get(listbox.curselection()))

listbox = Listbox(height=4)
fruits = ["Apple", "Pear", "Orange", "Banana"]
for item in fruits:
    listbox.insert(fruits.index(item), item)
listbox.bind("<<ListboxSelect>>", listbox_used)
listbox.pack()
window.mainloop()
```
# Layouts

There are three layout modifiers that can be used with Tkinter:

- Pack()
- Place()
- Grid()
## Pack()

This is the method we have been using to position our components thus far, it will place components in order from the chosen positioning. By default objects are placed from the top and center of the program downwards but it can be modified using the `side` argument to place objects in a different order.

For example `side = right`:

![](Pictures/Introduction%20to%20Tkinter%20-%20Pack%20Side%20Left.png)

Or `side = "right"`:

![](Pictures/Introduction%20to%20Tkinter%20-%20Pack%20Side%20Right.png)

## Place()

Place() allows us to specify exact x and y coordinates for our components.

![](Pictures/Introduction%20to%20Tkinter%20-%20Place%20Direction.png)

**Note:** Unlike the Turtle library objects are placed respective to the top left of the window, not the center.
## Grid()

Grid allows us to specify the location of objects along a grid. It is important to note however that this grid, in columns and rows, is *relative* to the first item in the grid. In other words, if your first item is placed at column 5 and row 5 it will stat at the top left of your window if there are no other objects placed before it.

Here is an example with:

- A label at column 0, row 0.
- A button at column 1, row 1.
- A second button at column 2, row 0.
- An entry box at column 3, row 2.

![](Pictures/Introduction%20to%20Tkinter%20-%20Grid.png)

# Padding

Padding can be added to components by passing the `padx` and `pady` keyword arguments.

For example a padding in both axis of 20 on the main window:

```python
window.config(padx=20, pady=20)
```

![](Pictures/Introduction%20to%20Tkinter%20-%20Padding.png)

Padding can be observed, black line is not present in the GU2I, only to visualize the padding.