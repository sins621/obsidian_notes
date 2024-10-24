# The Random Module

Like C++ Standard Libraries, we can import a library, or module, for random number generation.

```python
import random
```

Functions from this module can be accessed by using the module name and then appending it with a full stop.

```python
random.randint(a,b)
```

This function will return a random integer between the range given as arguments to the function.
## Random Float Generation

We can randomly generate float values from and including 0 to but not including 1 with the `random.random()` function.

We can manipulate this function for example to produce a number from and including 0 to but not including 10:

```python
random_number_0_to_10 = random.random() * 10
```

We can also generate random numbers between a specified range by using the random.uniform() function.

```python
random_float = random.uniform(1,10)
```

Note this will generate a floating point number between 1 and 10 but will also include 1 and 10.
# Lists

Isn't this just an array?

```python
fruits = ["Cherry", "Apple", "Pear"]
```
## Accessing List Elements

```python
print(fruits[0]) # Cherry
```

Negative indexes can also be used:

```python
print(fruits[-1]) # "Pear"
```
## Modifying List Elements

```python
fruits = ["Cherry", "Apple", "Pear"]
print(fruits[0]) # Cherry
fruits[0] = "Grapes"
print(fruits[0]) # Grapes
```
## Adding to The List

```python
fruits = ["Cherry", "Apple", "Pear"]
fruits.append("Grapes")
print(fruits[3]) # Grapes
```
### `extend()` function

```python
fruits = ["Cherry", "Apple", "Pear"]
fruits.extend("Grapes", "Bananas")
print(fruits[3]) # Grapes
print(fruits[4]) # Bananas
```
## Randomly Accessing a List Element
```python
import random
fruits = ["Cherry", "Apple", "Pear"]
print(random.choice(fruits))
```
# Nested Lists:

```python nums
fruit = [
    "Strawberries", 
    "Apples",
    "Grapes"
    ]

vegetables = [
    "Potatoes",
    "Spinach",
    "Tomatoes"
    ]

dirty_dozen = [fruit, vegetables]

print(dirty_dozen)
# Output
# [['Strawberries', 'Apples', 'Grapes'], ['Potatoes', 'Spinach', 'Tomatoes']]
```
## Accessing Nested List Elements

```python nums
fruits = [
"Strawberries", 
"Nectarines", 
"Apples", 
"Grapes", 
"Peaches", 
"Cherries", 
"Pears"
]

vegetables = [
"Spinach", 
"Kale", 
"Tomatoes", 
"Celery", 
"Potatoes"
]

dirty_dozen = [fruits, vegetables]

print(dirty_dozen[1][1]) # Kale
```

In this example the output is Kale because first we select which of the two lists we want to access and *then* only do we access one of the elements from that list. If you wanted to access the 2nd element of the first list you would need to do so as follows:

```python
dirty_dozen[0][1]
#           ^   Accessing First List
```