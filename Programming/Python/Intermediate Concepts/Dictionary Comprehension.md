New list inside a dictionary from an existing list:

```python nums
new_dict = {new_key:new_value for item in list}
```

New dictionary from existing dictionary:

```python nums
new_dict = {new_key:new_value for (key, value) in dict.items()}
```

With condition:

```python nums
new_dict = {
	new_key: new_value for (key, value) in dict.items() if condition
}
```

For example:

```python nums
from random import randint

names = ["Alex", "Beth", "Caroline", "Dave", "Eleanor", "Freddie"]

student_scores = {student: randint(1, 100) for student in names}

print(student_scores)
#{
#    'Alex': 22, 
#    'Beth': 23, 
#    'Caroline': 69, 
#    'Dave': 52, 
#    'Eleanor': 91, 
#    'Freddie': 77
#}
```

Example with condition:

```python nums
from random import randint

names = ["Alex", "Beth", "Caroline", "Dave", "Eleanor", "Freddie"]

student_scores = {student: randint(1, 100) for student in names}

print(student_scores)
#{'Alex': 70, 'Beth': 99, 'Caroline': 95, 'Dave': 94, 'Eleanor': 32, 'Freddie': 12}
passed_students = {
	student: score for (student, score) in student_scores.items() if score >= 80
}

print(passed_students)
#{'Beth': 99, 'Caroline': 95, 'Dave': 94}
```