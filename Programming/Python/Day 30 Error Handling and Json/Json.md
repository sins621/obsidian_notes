`Json` files are very broadly used data files with a data structure very similar to python dictionaries.

We can write, read and update json files by using the following methods.

```python
import json

website = website_entry.get()
mail = mail_user_entry.get()
password = password_entry.get()
new_data = {website: {"email": mail, "password": password}}

with open("./Day 30/Json Project/passwords.json", mode="r") as passwords:
	data = json.load(passwords)
	data.update(new_data)

with open("./Day 30/Json Project/passwords.json", mode="w") as passwords:
	json.dump(data, passwords, indent=4)
```

In this example we are getting the website, email address and password details from the user from a Tkinter GUI application.

From this data we create a dictionary to store their details called `new_data`.

We then open a `json` file and read it's values into a variable called `data` using the `json.load()` method. This will create a dictionary.

We can then update the dictionary with our new dictionary by calling the `json.update()` method, this method is important because it will maintain the structure of our dictionary, for example:

If we simply appended the dictionaries it may result in a data structure like this:

```json
{
    "website1": {
        "email": "bradlycarpenterza@gmail.com",
        "password": "password1"
    },
},
{
    "webstie2": {
        "email": "bradlycarpenterza@gmail.com",
        "password": "password2"
    }
}
```

This is not a valid `json` format, instead we want this:

```json
{
    "123": {
        "email": "bradlycarpenterza@gmail.com",
        "password": "123"
    },
    "dsads": {
        "email": "bradlycarpenterza@gmail.com",
        "password": "dsa"
    }
}
```

Finally we can update the `json` file with the contents of our new dictionary using the `json.dump()` method, the first argument to be passed is dictionary we are updating it with, the file we are writing to and additionally we provide an indent keyword argument so that the file is formatted with human readable indentation.

```python
with open("./Day 30/Json Project/passwords.json", mode="w") as passwords:
	json.dump(data, passwords, indent=4)
```