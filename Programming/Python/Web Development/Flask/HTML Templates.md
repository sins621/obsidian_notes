# Jinja HTML Templates
We can pass variables into our HTML files from our Python Server File using a templating language like *Jinja*

Fortunately Jinja comes bundled with Flask automatically, we can simply pass our variables in as follows:

```python
@app.route("/")
def home():
    random_number = randint(1, 10)
    year = time.year
    name = "Sins"
    return render_template(
        "index.html", random_number=random_number, year=year, name=name
    )
```

In this example we've passed 3 variables into our HTML file, a random number, the current year and my name.

To access these variables inside our HTML files we simply use double curly braces `{{}}`

```hmtl
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Website</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <h2>{{ 5 * 6 }}</h2>
    <h3>Random Number: {{random_number}}</h3>
  </body>
  <footer>
    <p>Copyright {{year}}, {{name}}</p>
  </footer>
</html>
```

And finally this is the result:

![](Pictures/HTML%20Templates%20-%20Jinja%20Templates.png)

# Multi-line Statements with Jinja

When we want to incorporate Multi-line Python statements in our HTML documents we need to use curly braces and percent signs for each line. `{%%}`

For example we can create a for loop which loops over blog posts we're fetching from an API:

```html
  <body>
    {% for blog_post in posts: %} 
    <h1>{{blog_post["title"]}}</h1>
    <h2>{{blog_post["subtitle"]}}</h2>
    {% endfor %}
  </body>
```

**Note**: It is important to signify the *end* of the for loop by using `{% endfor %}`

We can also use if statements with the same method:

```html
  <body>
    {% for blog_post in posts: %} 
    {% if blog_post["id"] == 2: %}
    <h1>{{blog_post["title"]}}</h1>
    <h2>{{blog_post["subtitle"]}}</h2>
    {% endif %} 
    {% endfor %}
  </body>
```

Just as before we signify the end of the if statement with `{% endif %}`.
# Building URLs with Flask and Jinja

We can use Flask and Jinja to create URLs to other web pages within our web site dynamically using the `url_for()` method:

```html
<a href="{{url_for('get_blog', num=3)}}">Go to blog</a>
```

This will navigate to the `get_blog` function we have created and pass `num` as a parameter.

```python
@app.route("/blog/<int:num>")
def get_blog(num):
    blog_url = "https://api.npoint.io/c790b4d5cab58020d391"
    print(num)
    response = get(url=blog_url)
    response.raise_for_status()
    all_posts = response.json()
    return render_template("blog.html", posts=all_posts)
```

In this example the parameter will be printed to the console.