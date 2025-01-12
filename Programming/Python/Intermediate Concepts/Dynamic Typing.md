# Introduction
Python is a **dynamically** typed language meaning that you don't need to specify the type of the variable and can alter it or reassign it to a different type later on.

```python
x = 1
print(x) 
x = "this is a string"
print(x)

# Output
#1
#this is a string
```

It is however **strongly** typed in that it enforces type rules strictly. You cannot perform invalid type operations.

```python
a = 1
b = "this is a string"
print(a+b)
#TypeError: can't concatenate str and int
```
# Example: Formatting a Timer

```python nums
def count_down(count):
    count_min = count // 60
    count_sec = count % 60

    if count_min < 10:
        count_min = f"0{count_min}"

    if count_sec < 10:
        count_sec = f"0{count_sec}"

    canvas.itemconfig(timer_text, text=f"{count_min}:{count_sec}")
    if count > 0:
        window.after(1000, count_down, count - 1)
```

In this example we create `count_min` and `count_sec` as integers however when we want the format for the timer to maintain two digits for minutes and seconds we can convert the integers to strings to prefix the integer with a string 0. 

Now for example when there are 4 minutes and 4 seconds remaining the output will be remain 04:04 instead of 4:4.