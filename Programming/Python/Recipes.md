# .env Files

## Installation of Python Dotenv Module

Install the Python Dotenv library by running the following command in your terminal or integrated terminal within your Python IDE.

pip install python-dotenv
### .env file

```
SECRET_KEY=mysecretkey  
DATABASE_URL=postgres://user:password@localhost/db  
API_KEY=your-api-key  
DEBUG=True
```
### File Structure

![ok](https://media.geeksforgeeks.org/wp-content/uploads/20240313112706/ok.png)

## Accessing Keys

```python
# Import the necessary module
from dotenv import load_dotenv
import os

# Load environment variables from the .env file (if present)
load_dotenv()

# Access environment variables as if they came from the actual environment
SECRET_KEY = os.getenv('SECRET_KEY')
```
# Pretty Print json

## [1. Python Pretty Print JSON String](https://www.digitalocean.com/community/tutorials/python-pretty-print-json#1-python-pretty-print-json-string)

```python nums
import json

json_data = '[{"ID":10,"Name":"Pankaj","Role":"CEO"},' \
            '{"ID":20,"Name":"David Lee","Role":"Editor"}]'

json_object = json.loads(json_data)

json_formatted_str = json.dumps(json_object, indent=2)

print(json_formatted_str)
```

Output:

```json
[
  {
    "ID": 10,
    "Name": "Pankaj",
    "Role": "CEO"
  },
  {
    "ID": 20,
    "Name": "David Lee",
    "Role": "Editor"
  }
]
```

- First, we use `json.loads()` to create the JSON object from the JSON string.
- The `json.dumps()` method takes the JSON object and returns a JSON formatted string. The `indent` parameter defines the indent level for the formatted string.

## [2. Python Pretty Print JSON File](https://www.digitalocean.com/community/tutorials/python-pretty-print-json#2-python-pretty-print-json-file)

Let’s see what happens when we try to print a JSON file data. The file data is saved in a pretty printed format.

![Json Pretty Printed File](https://journaldev.nyc3.cdn.digitaloceanspaces.com/2019/10/json-pretty-printed-file.png)

Json Pretty Printed File

```python nums
import json

with open('Cars.json', 'r') as json_file:
    json_object = json.load(json_file)

print(json_object)

print(json.dumps(json_object))

print(json.dumps(json_object, indent=1))
```

Output:

```json
[{'Car Name': 'Honda City', 'Car Model': 'City', 'Car Maker': 'Honda', 'Car Price': '20,000 USD'}, {'Car Name': 'Bugatti Chiron', 'Car Model': 'Chiron', 'Car Maker': 'Bugatti', 'Car Price': '3 Million USD'}]
[{"Car Name": "Honda City", "Car Model": "City", "Car Maker": "Honda", "Car Price": "20,000 USD"}, {"Car Name": "Bugatti Chiron", "Car Model": "Chiron", "Car Maker": "Bugatti", "Car Price": "3 Million USD"}]
[
 {
  "Car Name": "Honda City",
  "Car Model": "City",
  "Car Maker": "Honda",
  "Car Price": "20,000 USD"
 },
 {
  "Car Name": "Bugatti Chiron",
  "Car Model": "Chiron",
  "Car Maker": "Bugatti",
  "Car Price": "3 Million USD"
 }
]
```

It’s clear from the output that we have to pass the indent value to get the JSON data into a pretty printed format.
# Add Items to a Dictionary

```python nums
thisdict = {  
  "brand": "Ford",  
  "model": "Mustang",  
  "year": 1964  
}  
thisdict["color"] = "red"  
print(thisdict)
```