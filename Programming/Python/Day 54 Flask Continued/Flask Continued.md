# URL Parsing

Flask enables us to process the information entered into the URL bar, this is known as *URL Parsing*. For example we parse the name entered and use that to modify the output that we are serving to the browser:

```python
@app.route("/<name>")
def greet(name):
    return f"Hello {name}"
```

Now when we run our flask application and navigate to the URL it's running on and enter a name:

![](Pictures/Flask%20Continued%20-%20URL%20Parsing.png)

We can see that the address we enter is being used in the output. We can also modify the type that is returned from the URL by using a **Converter**:

| `string` | (default) accepts any text without a slash |
| -------- | ------------------------------------------ |
| `int`    | accepts positive integers                  |
| `float`  | accepts positive floating point values     |
| `path`   | like `string` but also accepts slashes     |
| `uuid`   | accepts UUID strings                       |

To use a converter simply prefix the variable with the type you would like to convert the variable to followed by a colon:

```python
@app.route("/<int:number>")
def greet(number):
    return f"Hello {number}"
```
# Debugging Flask Apps

Flask has a *debug mode* which allows us to have changes hot reloaded, see errors in the browser and also interact with a Python Debugger Console in the browser. To enable it we simply need to pass `True` into the debug parameter when we run our application:

```python
if __name__ == "__main__":
    app.run(debug=True)
```

Now when we save changes to the file and related files to our flask app our web application will be restarted however it is still important to remember to reload the web page in the browser.

Here is an example of an error view in debug mode:

![](Pictures/Flask%20Continued%20-%20Flask%20Error.png)

In order to open up the Python Shell we simply need to click on the Python Shell Icon next to our error and enter our debugger pin which can be found in the console where we've run our Flask Application.

![](Pictures/Flask%20Continued%20-%20Flask%20Python%20Shell.png)

# HTML Elements With Flask

We can also return HTML Elements via flask, well actually we have been already:

![](Pictures/Flask%20Continued%20-%20Hello%20World%20Elements.png)

We can see here in that Flask Structure's our Hello World string that we're returning into a full fledged HTML file ans supplies our string to the Body Tags. This means that because we are already providing HTML we can continue to provide more HTML elements if we wish.

```python
@app.route("/")
def hello_world():
    return "<h1 style='text-align: center'>Cool Heading</h1>" \
        "<img src='https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExdjdiZ24waDhxdmZndjc3czFwczY2c255eDI2MXRrMGd6YWVsOWFhMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/YHYmMLkOmqoo/giphy.gif' style='margin-left: 25%'>"
```

![](Pictures/Flask%20Continued%20-%20HTML%20Elements.png)

