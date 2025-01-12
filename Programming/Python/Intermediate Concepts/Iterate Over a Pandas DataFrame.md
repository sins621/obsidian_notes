If we turn our dictionary into a Pandas DataFrame we can iterate over the rows in our data frame using the `.iterrows()` function to create an iterable for our `for` loop.

```python nums
import pandas

student_dict = {
    "student": ["Angela", "James", "Lily"],
    "score": [56, 76, 98]
}

student_data_frame = pandas.DataFrame(student_dict)

for (index, row) in student_data_frame.iterrows():
    print(index)
    print(row)

# Output

# Index:
#0

# Row:
#student    Angela
#score          56
#Name: 0, dtype: object

# Index:
#1

# Row:
#student    James
#score         76
#Name: 1, dtype: object
 ```

We can also select a specific column from our row with the following method:

```python nums
for (index, row) in student_data_frame.iterrows():
    print(row.student)

# Output
#Angela
#James
#Lily
```