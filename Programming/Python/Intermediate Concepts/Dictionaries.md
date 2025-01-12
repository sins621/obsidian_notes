# Declaring Dictionaries

![](Pictures/Dictionaries%20Image%20Example.png)

- A Dictionary contains a **key** and a **value** which can be thought of as the word and it's meaning.

The syntax for Dictionaries in Python is as follows:

```python
{key: Value}
```

Say we were to substitute it for the values in our first entry in the example:

```python
{"Bug": "An error in a program that prevents the program from running as expected."}
```

If you would like to have multiple Dictionary entries you can separate them by comma:

```Python
{
"Bug": "An error in a program that prevents the program from running as expected.",
"Function": "A piece of code that you can easily call over and over again.",
"Loop": "The action of doing something over and over again.",
}
```

**Note:** It's common practice in Python to leave a trailing comma at the end of the last Dictionary entry.
# Accessing Dictionary Elements

```python
dictionary_name[key]

print(programming_dictionary["Bug"]) #An error in a program that prevents the program from running as expected.

# Incorrect Spelling:
print(programming_dictionary["Bog"]) # KeyError: 'Bog'

# Incorrect Data Type:
print(programming_dictionary[Bog]) # NameError: name 'Bog' is not defined

```
# Adding Dictionary Elements

```python
programming_dictionary = {
    "Bug": "An error in a program that prevents the program from running as expected.",
    "Function": "A piece of code that you can easily call over and over again.",
}

programming_dictionary["Loop"] = "The action fo doing something over and over again."
print(programming_dictionary)

# {
# 'Bug': 'An error in a program that prevents the program from running as expected.', 
# 'Function': 'A piece of code that you can easily call over and over again.',
# 'Loop': 'The action fo doing something over and over again.',
# }
```
# Declaring an Empty Dictionary

```python
empty_dictonary = {}
empty_dictionary["New Entry"] = "New description"
```
# Clearing Dictionary Contents

```python
programming_dictionary = {}
print(programming_dictionary) # {}
```
# Editing an Entry to a Dictionary

```python
print(programming_dictionary["Bug"]) # An error in a program that prevents the program from running as expected.

programming_dictionary["Bug"] = "A moth in your computer."
print(programming_dictionary["Bug"]) # A moth in your computer.
```
# Loop Through a Dictionary

```python
for thing in programming_dictionary:
	print(thing)
# Bug
# Function
# Loop
```

- The Loop Variable used to iterate through the dictionary will be assigned to the **key** value of the dictionary at that point in each iteration. 

```python
for key in programming_dictionary:
	print(key)
	print(programming_dictionary[key])

# Bug
# An error in a program that prevents the program from running as expected.
# Function
# A piece of code that you can easily call over and over again.
```