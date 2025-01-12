Large Python programs can be split up into user made modules which can then be imported into the main Python file.

For example say we have our main python file which is tasks.py and we have a second file called my_module.py:

my_module.py:
```python
my_favourite_number = 31
```

We can then import this module and access the variable from it:

tasks.py:
```python
import my_module

print(my_module.my_favourite_number) # 31
```

