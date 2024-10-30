# Classes

A Class is a blueprint that models the objects that will be created from it.

![](Pictures/OOP%20-%20Class%20Object%20Example.png)

## Creating a Class

```python
class User: 
	pass

user_1 = User()
```

- Declared using the `class` keyword.
- Indent expected after declaration, can use `pass` keyword if declaration will be empty.
## Adding Attributes to an Object in Class

An attribute is a variable that's associated with an object.

```python
user_1.id = "001"
user_1.username = "angela"

print(user_1.username) #angela
```
## Initializing an Object, Creating the Constructor

```python
class Car:
	def __init__(self):
		pass
```

- The `__init__` function will be called when the constructor syntax '`()`' is used when declaring the object. 

```python
class Car:
	def __init__(self):
		print("new user being created...")

user_1 = User()
user_2 = User()

# Output
#new user being created...
#new user being created...
```

- Other functions can also be called during initialization, in the above example the print function is called when both new objects are created.
## Adding Attributes to the Constructor

```python
class Car:
	def __init__(self, seats):
		self.seats = seats

my_car = Car(5) # Passing 5 through to seats
```

**Note:** You *must* always include attributes in your constructor call once you have included them in your definition, not doing so will result in a *TypeError*.
## Adding Default Attribute Values

```python
class User:
	def __init__(self, user_id, username):
		self.user_id = user_id
		self.username = username
		self.followers = 0

user_1 = User("001", "angela")
print(user_1.followers) #0
```
## Adding Methods to a Class

```python
class User:
	def __init__(self, user_id, username):
		self.user_id = user_id
		self.username = username
		self.followers = 0
		self.following = 0

	def follow(self, user):
		user.followers += 1
		self.following += 1

user_1 = User("001", "angela")
user_2 = User("002", "jack")

user_1.follow(user_2)
print(user_1.followers) #0
print(user_1.following) #1
print(user_2.followers) #1
print(user_2.following) #0
```

- The `self` keyword can be used to access the attributes of the object itself.
# Objects

Objects represent the actual code that will run in our software, the literal car in this example that will be driven.
## Creating an Object From a Blueprint

![](Pictures/OOP%20-%20Declaring%20Objects.png)

## Object Attributes

![](Pictures/OOP%20-%20Object%20Attributes.png)

### Accessing Object Attributes

```python
car.speed
^ Object

car.speed
     ^ Attribute
```

## Object Methods

![](Pictures/OOP%20-%20Object%20Methods.png)

### Accessing Object Methods

![](Pictures/OOP%20-%20Accessing%20Object%20Methods.png)
