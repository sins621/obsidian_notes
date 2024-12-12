# Scraping Web Pages

We can use the [**Beautiful Soup**](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) python library to parse HTML and XML files. 
```python
from bs4 import BeautifulSoup
```

By creating a `BeautifulSoup` object from a string of HTML we are afforded the ability to use various methods to access specific elements of a Web Page such as the headings, lists, links, etc.

```python
with open(f"{PATH}/website.html") as file:
    contents = file.read()

soup = BeautifulSoup(contents, "html.parser")
```

In this example we're parsing an HTML file by first reading it into a variable and then passing it in to the constructor along with the argument `"html.parser"` . We can also parse XML files but I don't remember the argument for that. 

## `find_all()`

We can find all the anchor tags for example by using the `find_all()` method:

```python
all_anchor_tags = soup.find_all(name="a")
# Output
#[<a href="https://www.appbrewery.co/">The App Brewery</a>, <a href="https://angelabauer.github.io/cv/hobbies.html">My Hobbies</a>, <a href="https://angelabauer.github.io/cv/contact-me.html">Contact Me</a>]
```

We can also narrow down our output by only targeting the links inside these anchor tags:

```python
for tag in all_anchor_tags:
    print(tag.get("href"))

# Output
#https://www.appbrewery.co/
#https://angelabauer.github.io/cv/hobbies.html
#https://angelabauer.github.io/cv/contact-me.html
```

# `find()`

We can target elements with a specific ID for example by using the `find()` method:

```python
heading = soup.find(name="h1", id="name")
print(heading)
# Output
#<h1 id="name">Angela Yu</h1>
```

Again, should we only want the text we can use the `get_text()` method:

```python
print(heading.get_text())
# Output
# Angela Yu
```

We can also target classes:

```python
section_heading = soup.find(name = "h3", class_="heading")
```

It is important to **note** however that that the `class_` argument is suffixed by an underscore to prevent conflict with the python `class` keyword.

## `select()`

We can also select elements by using CSS Selector syntax via the `select()` method.

```python
name = soup.select_one(selector="#name")
print(name)
# Output
#<h1 id="name">Angela Yu</h1>
```

`select_one()` returns the first match.

We can also return all matches for our CSS Selector parameter:

```python
heading = soup.select(".heading")
print(heading)
# Output
#<h1 id="name">Angela Yu</h1>
#[<h3 class="heading">Books and Teaching</h3>, <h3 class="heading">Other Pages</h3>]
```