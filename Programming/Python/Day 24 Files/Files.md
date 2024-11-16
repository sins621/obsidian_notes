# Introduction
The `open` and `read` functions can be used to interact with external files in python.

Say we have a `.txt` file named `my_file` containing:

> Hello, my name is Angela.

In our main.py file:

```python nums
file = open("my_file.txt")
contents = file.read()
print(contents) # Hello, my name is Angela.
file.close()
```

Note that it's important to `close` the file ourselves to ensure resources are freed up again to be used by the operating system.
# `with` keyword

The opening and closing of the file can be handled automatically using the `with` keyword.

```python nums
with open("my_file.txt") as file:
	contents = file.read()
	print(contents) # Hello, my name is Angela.
```
# Writing to a File

By default, using the `with` keyword, the file will be opened in *read-only* mode. To enable write operations on the file we can provide `"w"` as an argument for the `mode`.

```python nums
with open("my_file.txt", mode="w") as file:
	file.write("New text.")
```

Note this will erase all the contents of the file and write this new line to it. If you would like to append information to the file you can simply open it in append mode.

```python nums
with open("my_file.txt", mode="a") as file:
	file.write("\nNew text.")
```

`my_file.txt` contents:

```txt
Hello, my name is Angela.
New text.
```
# Creating Files

When you attempt to open a file in *write-mode* if the file does not exist it will then create the file for you.

```python nums
with open("new_file.txt", mode="w") as file:
	file.write("New text.")
```
