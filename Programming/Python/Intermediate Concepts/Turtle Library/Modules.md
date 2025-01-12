There are different ways to import modules in Python.

- `import` 'module'
- `from` 'module' `import` 'class'
- `from` 'module' `import` *
# `import` 'module'

When importing items this way you will need to prefix the class that you plan on accessing with the name of the module.

```python
import turtle

tim = turtle.Turtle()
```
# `from` 'module' `import` 'class'

Using this import method we can specify the class we want to import and then we don't need to prefix the class with the module name.

```python
from turtle import Turtle
```
# `from` 'module' `import` *

When importing modules this way we import *all* the classes of the module and don't need to prefix usage of classes with the module name, this however can can easily cause confusion in your code base as you could accidentally name variables, functions or classes after modules that are being imported that you aren't aware of.

```python
from random import *

choice = choice([1,2,3])
print(choice) # 1

choice = "cool_choice"
print(choice) # cool_choice
```
# Aliasing Modules

```python
import turtle as t

tim = t.Turtle()
```
# Installing Modules

Python ships with a core set of packages by default but we can download and install packages from the internet to extend the functionality of the language.

Say we want to use the '[heroes](https://pypi.org/project/heroes/)' package to generate random hero names.

We can use the `pip install heroes` command in our terminal to install the package via the python package manager, this will however install the module system-wide and arch linux for example will not allow you to do that. Instead we need to create a **virtual environment** for our project where we can install modules locally to that project. 

In the directory of your project run the following command:
``` shell
python -m venv
```

This will generate a bin directory inside your project along with the python interpreter and python package manager inside it. You can then use the python package manager inside of that bin directory to install modules for that project, for example:

``` shell
 ~/Documents/Python-Learning/bin/pip install heroes 
```

