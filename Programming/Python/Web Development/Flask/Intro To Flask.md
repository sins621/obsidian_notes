# Intro To Flask

Flask is light-weight framework that can be used to build web applications. Note the difference between a *framework* and a *library*:

|**Library**|**Framework**|
|---|---|
|Library is a set of reusable functions used by computer programs.|Framework is a piece of code that dictates the architecture of your project and aids in programs.|
|You are in full control when you call a method from a library and the control is then returned.|The code never calls into a framework, instead the framework calls you.|
|It’s incorporated seamlessly into existing projects to add functionality that you can access using an API.|It cannot be seamlessly incorporated into an existing project. Instead, it can be used when a new project is started.|
|They are important in program linking and binding process.|They provide a standard way to build and deploy applications.|
|Example: jQuery is a JavaScript library that simplifies DOM manipulation.|Example: AngularJS is a JavaScript-based framework for dynamic web applications.|
## 'Hello World' in Flask

```python nums
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"

if __name__=="__main__":
    app.run()
```

**Note:** It is necessary to `pip install flask` in your virtual environment.

First we import the Flask Library and create a Flask object called `app` by passing in the `__name__` variable.
### `__name__` Variable

In Python, `__name__` is a **special built-in variable** (a _magic_ or _dunder_ variable) that holds the name of the current module.
#### Technical Definition

The `__name__` variable in Python is:

- A **string** that represents the name of the module in which it is used.
- Its value depends on how the module is executed:
    - When a Python script is **executed directly**, `__name__` is set to `'__main__'`.
    - When a script is **imported as a module**, `__name__` is set to the name of the module.

---
#### Use Case

The value of `__name__` allows developers to write conditional code that executes only when a script is run directly and not when it is imported as a module.

For example:

```python
def my_function():
    print("This is a function in the script.")

# Check if the script is run directly
if __name__ == "__main__":
    print("Script is run directly")
    my_function()
else:
    print("Script is imported as a module")
```

---
#### Output Scenarios

1. **When run directly as a script**:
    
    ```bash
    python script.py
    ```
    
    **Output**:
    
    ```
    Script is run directly
    This is a function in the script.
    ```
    
2. **When imported as a module**: If the script above is imported in another script:
    
    ```python
    import script
    ```
    
    **Output**:
    
    ```
    Script is imported as a module
    ```
    

---
#### Summary

- `__name__` is a special variable that represents the module name.
- When the script is executed directly, `__name__` equals `'__main__'`.
- When the script is imported, `__name__` equals the name of the script/module.

This distinction is especially useful for separating executable code from reusable code in Python scripts.

### Running Our Flask Application

As previously mentioned we are running our Flask app inside the if check for if the special name variable is main therefore when running our script directly the `run()` method will be called on our `app` object resulting in the following:

![](Pictures/Intro%20To%20Flask%20-%20Running%20Flask.png)

All we need to do to see our web app that was created is to navigate to the *local* IP address provided by Flask:

![](Pictures/Intro%20To%20Flask%20-%20Hello%20World.png)

And As you can see our browser has submitted a get request and the HTML that we are returning from our function is served to the browser.

## Python Decorators

Decorators can be used to abstract functionality that we want to apply to different functions.

For example we could create a delay decorator to add a time delay to functions:

```python
def delay_decorator(function):
	def wrapper_function():
		time.sleep(2)
		# Calling the Function being Decorated
		function()
	return wrapper_function

@delay_decorator
def say_hello():
	print("Hello")

say_hello()
```

By using the `@` symbol prior to calling the `say_hello()` function we will be applying our delay_decorator to this function when it is called. The function will automatically be passed into our decorator function, delayed for 2 seconds and then executed.

This simplifies the entire process which would look something like this:

```python
def delay_decorator(function):
	def wrapper_function():
		time.sleep(2)
		# Calling the Function being Decorated
		function()
	return wrapper_function

def say_hello():
	print("Hello")

call_say_hello = delay_decorator(say_hello)
call_say_hello()
```

Here we first need to store the function that is nested inside the `delay_decorator` function inside of a variable and then call it using parenthesis which will trigger the delay and call the original function itself.
### Decorators in Flask

```python
@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"
```

Here our `hello_world()` function is being decorated with the `route()` method from our `app` object. This enables us to associate a function with a route and as a result when we navigate the `/` route, also known as the *home* route, the hello world function will be called returning our simple 'Hello World' html.
