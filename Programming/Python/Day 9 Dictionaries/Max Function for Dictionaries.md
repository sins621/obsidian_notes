Python has a helpful function called `max()` for finding the maximum value in a dictionary.

```python
fruits = {"apple": 2, "pear": 4, "orange": 9}
max(fruits, key=fruits.get) # orange
```