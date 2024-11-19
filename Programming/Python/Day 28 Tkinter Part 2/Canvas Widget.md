# Introduction

The example project today is to create a pomodoro tracker using Tkinter which should look as follows:

![](Pictures/Canvas%20Widget%20-%20Pomodor%20Timer%20Complete.png)

To embed our tomato image with a text item on top of it we will be using the Canvas widget.

The `Canvas()` class can be called to create a canvas object which we can use to embed other widgets.
# Creating The Canvas

First we create a canvas object and the first two keyword arguments for width and height:

```python
from tkinter import *

canvas = Canvas(width=200, height=224)
```

We have chosen these dimensions because our tomato.png file has a width of 200px and height of 223px.

Next we can create a `PhotoImage()` object to place our image inside:

```python
tomato_img = PhotoImage(file="./Day 28/pomodoro/tomato.png")
```

Then we add that image to our canvas using the `create_image()` method:

```python
canvas.create_image(101, 112, image=tomato_img)
canvas.pack()
```

Naturally we call the `pack()` method to place the canvas inside of our window. Finally we add text to our canvas by calling the `create_text()` method.

```python
canvas.create_text(
	101, #xpos
	125, #ypos
	text="00:00",
	fill="white",
	font=(FONT_NAME, 35, "bold")
	)
```

**Note:** Some constants are in use here.

Now we should see the following:

![](Pictures/Canvas%20Widget%20-%20Canvas%20Item.png)

# Changing Background Color:

In order to change the background color of our window and canvas we will need to pass a value for the `bg` keyword arguments.

First let's update our window config:

```python nums {5}
from tkinter import *

window = Tk()
window.title("Pomodoro")
window.config(padx=100, pady=50, bg=YELLOW)
```

**Note:** `YELLOW` is a constant for a hex code color.

Next we update our canvas constructor.

```python
canvas = Canvas(width=200, height=224, bg=YELLOW)
```

We should now have the following:

![](Pictures/Canvas%20Widget%20-%20BG%20Changed.png)

However, you may be able to notice a faint white outline for our canvas, in order to remove this we are going to need to set the value for the `highlightthickness` keyword argument to 0.

```python
canvas = Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)
```

We should now have the following, updated to remove the outline:

![](Pictures/Canvas%20Widget%20-%20Canvas%20Final%20BG%20Changed.png)

