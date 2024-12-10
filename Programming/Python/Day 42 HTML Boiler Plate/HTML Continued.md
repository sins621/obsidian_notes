# Basic Boilerplate

![](Pictures/HTML%20Boiler%20Plate%20-%20Basic%20Boiler%20Plate.png)
# Lists

![](Pictures/HTML%20Lists%20-%20HTML%20Lists.png)

- `<ul></ul>` is used for *Unordered Lists*.
- `<li></li>` is used to denote a *List Item*.
- `<ol></ol>` is used to denote an *Ordered List*.
# Nesting and Indentation

![](Pictures/HTML%20Continued%20-%20Nested%20Lists.png)

It is also possible to create *Nested Lists* by nesting a new list inside an existing one.
# Anchor Elements (Hyperlinks)

We can create hyperlinks by using anchor tags `<a></a>` and providing attributes, such as the URL, to it.

```html
<h1>My top 5 Favourite Websites</h1>
<ol>
  <li><a href="https://youtube.com">Youtube</a></li>
  <li><a href="https://twitch.com">Twitch</a></li>
  <li><a href="https://amazon.com">Amazon</a></li>
  <li><a href="https://9gag.com">9gag</a></li>
  <li><a href="https://9anime.com">9anime</a></li>
</ol>
```

![](Pictures/HTML%20Continued%20-%20Hyperlinks.png)

# Image Element

The `img` element can be used to display an image in your webpage:

```html
    <img
      src="https://raw.githubusercontent.com/appbrewery/webdev/main/birthday-cake3.4.jpeg"
      alt="Birthday Cake"
    />
```

Use the `src` attribute to specify the source of the image, in this example it is from a web page. Use the `alt` attribute to specify a name or description for the image so that accessibility software can inform the user of the contents of the image.