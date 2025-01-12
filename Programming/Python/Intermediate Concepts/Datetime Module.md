In order to work with time easily or access the current time when the program is run we can use the `datetime`.

```python nums {3,8}
import datetime as dt

now = dt.datetime.now()
year = now.year
day_of_week = now.weekday()
print(day_of_week) # 5

date_of_birth = dt.datetime(year=1997, month=2, day=18)
print(date_of_birth) # 1997-02-18 00:00:00
```

On line 3 we create a new `datetime` object calling the `now()` method. We can then access attributes such as the year, month, day etc from this object which will be equivalent to the current date and time of operation.

We can also create our own `datetime` objects by initializing them with at minimum the year, month and day which allows us to use the same formatting and methods available from the module.