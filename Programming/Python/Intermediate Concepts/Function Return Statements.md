# Declaration

```python
def my_function():
	result = 3 * 2
	return result
```
# Multiple Return Values

```python
def format_name(f_name, l_name):
    if f_name == "" or l_name == "":
        return "You did not provide valid inputs"
    
    return str(f_name + " " + l_name).title()
```

In this example the function returns before any processing takes place in the event that either a first name or last name isn't provided.

