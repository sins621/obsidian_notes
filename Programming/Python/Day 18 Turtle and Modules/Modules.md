Modules can be imported using the following keywords:

- `import` 
- `from` 'module' `import` 'item'
- `from` 'module' `import` *
# `import`

We can import all the contents of the module using the `import` keyword.

```python
   import turtle
#  ^ keyword
   import turtle
#         ^ module name

# create object
tim = turtle.Turtle()
```
# `from` 'module ' `import` 'item'

If we wish to only use specific items from the module we can use the `from` 'module' `import` 'item' syntax.

```python
from turtle import Turtle

tim = Turtle()
tom = Turtle()
terry = Turtle()
 ```
# `from` 'module' `import` * 