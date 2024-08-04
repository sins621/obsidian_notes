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

