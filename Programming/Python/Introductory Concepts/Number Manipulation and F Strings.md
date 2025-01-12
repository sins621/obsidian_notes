# The `round()` Function

```python
bmi = 84 / 1.65 ** 2
print (bmi) # 30.85399449035813
print (int(bmi)) # 30
print (round(bmi)) # 31
```

We can use the `round()` function in this instance to return a type `int` that will then have the returned value rounded.

`round()` can also take two arguments, the first being the number that we intend to round and the second being the number of digits we intend to round to.

```python
print(round(bmi,2)) # 30.85
```

# Mathematical Assignment

We can perform a mathematical operation on a variable and assign the value of that operation to the variable using one operator.

- `+=`
- `-=`
- `*=`
- `/=`

For example:

```python
score = 0
print(score) # 0
score += 1
print(score) # 1
```

# F-Strings

F-Strings can be used to combine different data types inside strings and have them be automatically type casted to a string.

```python nums
score = 0
height = 1.8
is_winning = True

print(f"Your score is = {score}, your height is {height}. You are winning is {is_winning}")
```

Note that variables are to be surrounded by curly brackets.