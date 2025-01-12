# PDB - The Python Debugger

The python debugger can be accessed simply by running your program with the python command and then adding `breakpoint()` at the point where you would like the program to break.

```python nums
foo = "bar"

while True:
	print(foo)
	breakpoint() # Program will break here
```

![](Pictures/Debugging%20-%20Breakpoint.png)

The debugger will show the line number and line of code being executed after the breakpoint.
## Printing Variables

We can print the value of variables using the `p` command followed by the variable name.

![](Pictures/Debugging%20-%20Print%20Variable.png)




