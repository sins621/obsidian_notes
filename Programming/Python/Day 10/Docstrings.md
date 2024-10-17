```python
def format_name(f_name, l_name):
    """Take a first and last name and ofrmat it to return the
    title case version of the name."""
    if f_name == "" or l_name == "":
        return

    return str(f_name + " " + l_name).title()
```

![](Pictures/Docstrings%20-%20Docstring%20Tooltip.png)

By using Docstrings we are able to add information to the tooltip shown when hovering a function name in our editor. 