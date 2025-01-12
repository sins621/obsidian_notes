# Introduction

```python
{
Key: [List],
Key2: {Dict},
}
```

 In this example we have a List as the value for the first **Key** and another Dictionary as the value for the second **Key**.

```python
nested_list = ["A", "B", ["C", "D"]]
```

In this example we have a list inside of a list.
# Accessing Nested Data Structure Elements

```python
travel_log = {
    "France": ["Paris", "Lille", "Dijon"],
    "Germany": ["Stuttgart", "Berlin"],
}

print(travel_log["France"][1]) # Lille
```

In this example because we are trying to access a **List** nested inside of a **Dictionary** we will first call the Dictionary **Key** followed by the list **Index** of the item we are trying to access.

```python
nested_list = ["A", "B", ["C", "D"]]

print(nested_list[2][1]) # D
```

In this example we are trying to access the second element of the list that is **nested** at the third index of the first list. We will access this by calling the list name followed by the first index, the the second index which is the index of the second item inside of the nested list.

```python nums
travel_log = {
    "France": {
        "num_times_visited": 8,
        "cities_visited": ["Paris", "Lille", "Dijon"],
    },
    "Germany": {
        "cities_visited": ["Berlin", "Hamburg", "Stuttgart"],
        "total_visits": 5
    } 
}

print(travel_log["Germany"]["cities_visited"][2]) # Stuttgart
```

In this example we are trying to access **Stuttgart** which is a list element nested inside a dictionary which is nested inside another dictionary.