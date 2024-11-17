# Introduction
When creating methods/functions in python we can create *advanced* arguments.

Say we have a function with multiple arguments where each argument has a **default** assignment.

```python
def my_function(a=1, b=2, c=3)
	#Do this with a
	#Then do this with b
	#Finally do this with c

my_function(b=5)
```

In this example `my_function` has 5 passed in to the argument `b` therefore it will be run with the following arguments: `my_function(a=1, b=5, c=3)`
# `*args`

Say we had a function that adds numbers, in this case it's able to add two numbers:

```python
def add(n1, n2):
	return n1+n2

add(n1=5, n2=3)
```

What if we wanted to add 3 numbers? or 5? or 20? We would then need to create `n*arguments` which would be a hassle.

```python
def print_args(*args):
	for n in args:
		print(n)

print_args(1,2,3,4,5)

# Output
#1
#2
#3
#4
#5
 ```

The asterisk allows us to specify as many arguments as we like and then iterate through them inside of the function body.

**Note:** The arguments will be passed in as a ==tuple==. This means that you are able to access items at a specific position inside this tuple and so it can be import that arguments are given in the correct order.

```python
def print2(*args):
	print(args[2])

print2("no", "no", "this one") #this one
 ```
# `**kwargs`

We can also pass in unlimited **keyword arguments** by using the double asterisk, this will create a ==dictionary== where our argument names will be stored as the keys and values passed in will be the values.

```python
def kwargs(**kwargs):
	print(type(kwargs))

kwargs() # <class 'dict'>
```

This means we can access keys for our operations the same way we would with any normal dictionary.

```python
def calculator(n, **operations):
    n += operations["add"]
    n *= operations["multiply"]
    return n

print(calculator(2, add=3, multiply=3)) #15
```
# Creating Classes with Kwargs

We can also initialize class variables with keyword arguments as follows:

```python
class Car:
	def __init__(self, **kw):
		self.make = kw["make"]
		self.model = kw["model"]

my_car = Car(make="Nissan", model="GT-R")
print(my_car.model) #GT-R
```

Not however that when we access dictionary elements this way failing to provide all the keys that are being accessed will result in an error:

```python
my_car = Car(make="Nissan")
# Output
#KeyError: 'model'
```

Instead we can use the `.get()` method for accessing dictionary items, in the event that the key wasn't provided it will return `None`

```python
class Car:
	def __init__(self, **kw):
		self.make = kw.get("make")
		self.model = kw.get("model")
		self.colour - kw.get("colour")
		self.seats = kw.get("seats")

my_car = Car(make="Nissan")
print(my_car.model) #None
```