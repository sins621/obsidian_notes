Godot is a high-level, object-oriented, imperative, gradually typed programming language built for Godot with Python-like syntax.

# Function `_ready()`

Think of this as the beginning of the game, this function is called when the node enters the scene tree for the first time.

By default you will find the `pass` keyword. `Pass` means do nothing and you will find it in functions that have no code written in it.

## Hello, world!

To print "Hello, world!" we can simply use the `print()` function.

# Syntax

There is no need to add a semi-colon at the end of code lines like in other languages. Also note that GDScript uses indentation to determine the structure of your code. For example:

```gdscript
func _ready()
	print("Hello, world!")
```

Because `print()` has been indented under `func _ready()` this means that it is part of the `ready()` function.

GDScript is also **case-sensitive** meaning `Print()` would result in an error in this instance.

# Modifying Nodes (1.0)

First add a node to modify, you can use a label.


![[Add Label Node.png]]
![[Center Label.png]]
![[Enlarge the Label.png]]
![[Write Text and Center.png]]
![[Override Font Size.png]]
## Edit the Text of the Label through Script

Before we can edit the label through script, we need two things. We need a reference to the label, and we need to access the property in the label that we need to change. In this case, the `text` property.

![[Text Property on Hover.png]]

Hovering over the Text property in the Inspector displays the property to be used in script.

You can reference `Label` in the `main.gd` script by dragging the node into the script.
![[Reference to Node by Drag.png]]
Then you can access the text property and update it by using `.text` and the assignment operator `=`.

## Editing color through Script

Let's use this method to change the color of the text. There is a property called `modulate` which allows us to tint Sprites and UI elements. Using the same method of referencing Label as we have before we can change the color of the text with the following line:

```gdscript
$Label.modulate = Color.GREEN
```

Congratulations, you have successfully printed a green "Hello, world!".
![[Green Hello, world.png]]

# Input

Let's say we wanted to turn the label red when pressing the space-bar key. To do this we first need to set up an `input-action`.

Navigate to `Project`, `Project Settings` and then `Input Map`
![[Input Map Settings.png]]
Here we can add `Actions`. Actions allow us to bind keys to something we want to happen.

First type the name of the action under `Add New Action`, press the `Add` key. Then press the `+` button next to the action you have created to assign a keybinding to it.
![[Assign Action.png]]
## Create an Input Function

Write the following line beneath the `_ready()` function but **not** indented within it.

```gdscript
func _input(event):
	pass
```

Just like `_ready()` this is one of the built in functions of Godot. Instead of being called at the start of the game, it runs when the game receives any input, such as when we press a button. `event` is where we call for the information relating to what triggered the function.

Let's check if the event that triggered the input was our action that we pressed. We can use the following line:

```gdscript
func _input(event):
	if event.is_action_pressed("my_action"):
```

Now, let's use this if statement to change the color of our label to red when pressing the key and back to green when releasing the key. Just as before, reference the Label Node by dragging it into the text editor:

```gdscript
func _input(event):
	if event.is_action_pressed("my_action"):
		$Label.modulate = Color.RED
	if event.is_action_released("my_action"):
		$Label.modulate = Color.GREEN
```

# Variables (1.0)

Variables are essentially containers that hold information.

In the case of a **Player Character** we could use variables to hold information as as the **name**, **health**, **damage**, and if the player is **alive or not**.

Let's make a **Health** variable:

Near the top of our script we can declare a health variable and then print it's value in the `_ready()` function.

```gdscript
var health = 100

func _ready():
	print(health)
```

## Modifying Variables
We can also make changes to our variable before printing it such as assigning a new value:
```gdscript
var health = 100

func _ready():
	health = 40
	print(health)
```

Assign to a calculation:
```gdscript
var health = 100

func _ready():
	health = 20+30
	print(health)
```

Add:
```gdscript
var health = 100

func _ready():
	health += 20
	print(health)
```

Subtract:
```gdscript
var health = 100

func _ready():
	health -= 10
	print(health)
```

Multiply:
```gdscript
var health = 100

func _ready():
	health *= 4
	print(health)
```

Divide:
```gdscript
var health = 100

func _ready():
	health /= 20
	print(health)
```

## Adjusting Variable Values with an Input Actions

Let's look at an example where our player takes some damage and we want to subtract the damage from our health. Let's try decreasing our health value whenever we press the action we created earlier.

```gdscript
var health = 100

func _input(event):
	if event.is_action_pressed("my_action"):
		health-=20
		print(health)
```

# If-statements (conditionals)

If statements are the glue that holds all of our logic together. We've already used if statements to check if our action was pressed, but they can do so much more. An if statement is just a condition that needs to be met in order for the code inside of it to execute.

Let's add an if statement to check if our health reaches zero:
```gdscript
var health = 100

func _input(event):
	if event.is_action_pressed("my_action"):
		health-=20
		print(health)
		if health <= 0:
			health = 0
			print("YOU DIED!")
```

Here we are using `<=` to compare our health to the value however, there are many more comparisons we can use.

| Comparison Sign | Description                 |
| --------------- | --------------------------- |
| X == Y          | IS EQUAL TO                 |
| X != Y          | IS NOT EQUAL TO             |
| X > Y           | IS GREATER THAN             |
| X < Y           | IS LESS THAN                |
| X >= Y          | IS GREATER THAN OR EQUAL TO |
| X <= Y          | IS LESS THAN OR EQUAL TO    |

We can also add more conditions to our if statements. We can use the `and` keyword to execute if both conditions are met as well as the `or` keyword to execute if either or of the conditions are met.

One of the powerful features of if statements is not only can we define what code executes when it is true, but also what executes when it is false. We do this using the `else` keyword.

Let's add an else to print that we are still alive if our health hasn't reached zero yet:
```gdscript
var health = 100

func _input(event):
	if event.is_action_pressed("my_action"):
		health-=20
		print(health)
		if health <= 0:
			health = 0
			print("YOU DIED!")
		else:
			print("YOU ARE HEALTHY.")
```

Even cooler is that we can chain together if statements using else if statements or in the case of gdscript `elif` statements.

Let's add an else if to notify the player that they are injured when their health goes below 50.

```gdscript
var health = 100

func _input(event):
	if event.is_action_pressed("my_action"):
		health-=20
		print(health)
		if health <= 0:
			health = 0
			print("YOU DIED!")
		elif health < 50:
			print("YOU ARE INJURED")
		else:
			print("YOU ARE HEALTHY.")
```

Note that the if statements we have created are nested inside another if statement. You can easily layer if statements to get more advanced functionality however, try not to overdo it. You can quickly get lost in the ifs.

# Comments

We use comments to help explain the what and the why of our code. Adding a comment is simple and can be done above or after a line using the `#` symbol.

```gdscript
func _ready():
	# This is a comment about code that follows
	print("Hello, world!") # This is a comment about this line only
```

We can also use comments to temporarily disable lines of code and it's good practice to omit the space to indicate that it is a line of code.

```gdscript
func _ready():
	# This is a comment about code that follows
	print("Hello, world!") # This is a comment about this line only
	#print("I'm not sure about this...")
```

To comment out multiple lines of code simply highlight them with your mouse cursor, right click and select the option.
![[Toggle Comment.png]]
# Variables 2.0

When declaring a variable we need to think about where we do so. if we declare a variable inside an if statement for example we can only use the variable inside **that** if statement. This is called _scope_. If you want to use variables in many places in your script make sure to declare it at the top so that it is a script wide variable, meaning it can be accessed anywhere within your script.

```gdscript
extends Node

var script_variable = 100

func _ready():
	pass
```

If you were to declare it inside the function then you would only be able to use it within that function.

```gdscript
extends Node

func _ready():
	var script_variable = 100
```

A cool thing about variables inside of GDScript is that you can declare them without thinking about what type of data is inside them. 

```gdscript
	var godot_is_cool = true
	var coolness = 9001
```

We can even change the type of data that they hold just by reassigning them.

```gdscript
	var godot_is_cool = true
	var coolness = 9001
	coolness = true
```

That being said, we still need to be aware of what type of data we are working with. Some parts of our game may expect a specific type of data and we will get an error of we do not convert the data.

In GDScript we have the four classic data types, namely: boolean, integer, float and string. Converting from one type to another is called `Casting`. 

For example we can cast an integer into a string. Say we have a number and a string and we would like to add the number to the string. We can use the `str()` function to cast the integer to a string.
```gdscript
var number = 42
var text "Meaning of life: " + str(number)
print(text)

# Output
# The meaning of life: 42
```

We can do a similar thing to convert a float to an integer. Say we have a variable called `pi` that is equal to 3.14 and we want to convert it to an integer. We can use the `int()` command in this case.
```gdscript
var pi = 3.14
print(int(pi))
```

Just note that this will truncate the float and lose the information after the decimal point.

Other common data structures in GDScript are Vector2 and Vector3. Vector2 stores two floats, namely `x` and `y`. And Vector3 stores 3 floats, namely `x`, `y` and `z`. 
```gdscript
var vec2 = Vector2(0.0, 0.0)
var vec3 = Vector3(0.0, 0.0, 0.0)
```

These are most commonly used for positions. We can create a variable called position with some coordinates which we can then modify by modifying position's components like it's `x` coordinate. 

Let's declare and initialize a Vector3 called position, add 2 to it's `x` coordinate and print the entire vector.
```gdscript
var position = Vector3(3, -10, 5)
position.x += 2
print(position)

# Output
# (5, -10, 5)
```

By default GDScript is what we call dynamically typed. This means that we don't define what type of data a variable can hold when we declare it. This is what we've been using so far. This makes it fast to create variables and flexible because we can reassign data of another type at will. However it is also more prone to error, and less performant than static typing. Luckily, GDScript allows us to statically type any variables we want.

To statically type a variable, we simply add the type when declaring it:
```gdscript
var damage: int = 15
```

We can also have Godot determine the data type by writing `:=` and then the value:
```gdscript
var damage := 15
```

This is called inferred typing and the result is exactly the same. The variable is still static, Godot simply recognizes in this case that 15 is a whole number and sets the variable to a type of `int`.

This also means that the variable can not change to another type. If you were to try and set it to a string in this instance, you would get an error.
![[Illegal Typing Error.png]]
Adding `@export` in front of a variable will allow us to set it using the inspector. The value we save in the script will just be the default value.
![[Variable in Inspector.png]]

Sometimes you want to define a variable that cannot change. For this we use a constant:

```gdscript
const GRAVITY = -9.81
```

It's standard practice to name constants with capital letters.

We can try to change the value of `GRAVITY` like any other variable but if we do that we will be presented with an error:
![[Const Reassign Error.png]]
# Functions

Functions are the bread and butter of programming, they allow you to bundle your code into small reusable packages. so far we have been using some of Godot's built in functions like `func _ready():` and `func _input():`. Notice how these are prefixed with an underscore. This is to show that they are not activated or called by us but by the engine itself. 

We can actually make our own functions and use them to do really cool things. Common functions to making games are things like `func jump()`, `func die()`, `func shoot()` and `func respawn()`. Making a function is actually really easy.

Let's make a function for jumping:
```gdscript
extends Node

func jump():
	# add upwards force
	# play a boioioioing sound
	# play a jump animation
	print("JUMP!")
```

Nothing is currently triggering or "Calling" our function. Let's call it whenever we press the action we made earlier.

```gdscript
extends Node

func _input(event):
	if event.is_action_pressed("my_action"):
		jump()

func jump():
	# add upwards force
	# play a boioioioing sound
	# play a jump animation
	print("JUMP!")

# Output when pressing space:
# JUMP!
```

