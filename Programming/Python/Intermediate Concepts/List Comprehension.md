Creating a new list from a For Loop
# Introduction

```python nums
numbers = [1, 2, 3]
new_list = []
for n in numbers:
	add_1 = n + 1
	new_list.append(add_1)
```

Creating a new list with List Comprehension

```python nums
new_list = [new_item for item in list]
```

Adapting to the example above:

```python nums
numbers [1, 2, 3]
new_list = [n+1 for n in numbers]
# new_list = [2, 3, 4]
```
# Other Use Cases

Note this can also be used on other data types like *strings*

```python nums
name = "Angela"
new_list = [letter for letter in name]
```

It can also be used for other iterables such as *range*

```python nums
numbers = []

for i in range(1, 5):
    numbers.append(i*2)

print(numbers) #[2, 4, 6, 8]
 ```

```python nums
numbers = [i*2 for i in range(1, 5)]

print(numbers) #[2, 4, 6, 8]
```
# Conditional List Comprehension

```python nums
new_list = [for new_item for item in list if condition]
```

Say we have a list of names and we want to create a new list that only contains names that are 4 characters or less.

```python nums
names = ["Alex", "Beth", "Caroline", "Dave", "Eleanor", "Freddie"]

short_names = [name for name in names if len(name) <= 4]

print(short_names) #['Alex', 'Beth', 'Dave']
```