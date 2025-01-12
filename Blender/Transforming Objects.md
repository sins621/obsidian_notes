# Properties Editor Transform Controls:

Move Along X Axis:
![](Pictures/Rotate%20Along%20X%20Axis.png)

Values can also be adjusted by:

- Clicking and dragging left and right on the value.
- You can enter math inside the value as well for example `2 + 5` would adjust the value to 7.
- Alternative units can also be entered if the correct notation is used for example `5cm` would move the unit 5cm to the x axis in this instance. It will also do conversion if a different system is used for example feet to meters.

![](Pictures/Changing%20Units.png)
The Unit System can be adjusted by navigating to `scene` > `Units` in the Property Editor.

![](Pictures/Left%20Click%20Drag%20to%20Adjust%20Values.png)

You can left click and drag down to adjust multiple values in a collection. The collection can be **reset to default values** by hovering over the collection and pressing `backspace`.

Scale Transform:
![](Pictures/Scale%20Transform.png)

# Tool Transform Controls:

## Move Tool:
![](Pictures/Move%20Tool.png)

Move items along different axis by left clicking and dragging on the axis arrow heads.

Other Methods of Moving:
![](Pictures/Other%20Moving%20Tools.png)
## Rotate Tool:
![](Pictures/Rotate%20Tool.png)

### Rotate in Increments:

![](Pictures/Rotate%20in%20Increments.png)

Rotation can be done incrementally by holding `ctrl` while left clicking and dragging.

### Rotate with finer control:

Holding down `shift` while rotating will make fine adjustments.

## Scale Tool:
![](Pictures/Scale%20Tool.png)

Adjust Scale by left clicking and dragging on the Square Icon of the corresponding Axis.

Scale Cage Subtool:
![](Pictures/Scale%20Cage.png)

Allows you to scale the object in the same manner as you would an image in a photo editor.

## All-in-one Tool:
![](Pictures/All-in-one%20Tool.png)

Allows you to move, rotate and scale all in the same Gizmo.

![](Pictures/Object%20Gizmos.png)

Gizmos can be toggled on so that they are visible and adjustable regardless of the selected tool.

![](Pictures/Reset%20Transform.png)

All Location, Rotation and Scale values can be reset by navigating to `Object` > `Rotation` > `Scale`. Hotkeys can also be used: `Alt G` for Location, `Alt R` for Rotation and `Alt S` for scale.

![](Pictures/Object%20Mouse%20Transform%20Shortcut.png)

Shortcuts can be used to transform selected objects with the mouse. This will temporarily engage the the corresponding transform until left mouse is clicked. Hotkeys can also be used here. Namely, `G` for Move, `R` for Rotate and `S` for Scale.

# Key Stroke Combinations:

A combination of keystrokes can be used to make adjustments to the transform without adjusting the Property Editor.

It can be done in the following 3 stages:

1. First, Press the hotkey of the corresponding transformation:

`G` For Move
`R` For Rotate
`S` For Scale

2. Constrain transformation to a corresponding Axis:

`X` for X Axis
`z` for Z Axis
`Y` for Y Axis

Note: If no Axis is selected then you will be making an adjustment to all Axis.

3. Use number keys to make adjustments in numbered increments.

Entering a number after the first two stages have been completed will transform the object by the entered number along the selected plane by the unit value selected. Confirm by pressing enter.

# Last Adjusted Panel:

![](Pictures/Adjust%20Last%20Operation.png)

When making an adjustment to the transform values a panel will show up showing the property of the last adjustment made.

![](Pictures/Adjust%20Last%20Operation%20Challenge.png)

If you don't see the window simply navigate to `View` > `Adjust Last Operation`

