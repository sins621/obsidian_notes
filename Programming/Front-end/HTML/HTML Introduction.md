# Web Browser Files:

- **HTML**
- **CSS**
- **JavaScript**

**HTML:** Hyper Text Markup Language

Purpose: Responsible for the structure of your website.

**CSS:** Cascading Style Sheets

Purpose: Responsible for Styling the HTML.

**JavaScript:** High-level programming language.

Purpose: Responsible for the logic of your website.
## HTML 

Describes the structure of a page using *tags* and *elements*.

![](Pictures/The%20Internet%20-%20Tags%20and%20Elements.png)

### Headings:

Headings in HTML function the same as they would in a book, or as in this markdown file, for example:
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6

They are used to display how many levels you are deep into a document, the equivalent in HTML would look like this:

```html
<h>Heading 1</h>
<h>Heading 2</h>
<h>Heading 3</h>
<h>Heading 4</h>
<h>Heading 5</h>
<h>Heading 6</h>
```

**Note:** 
- Heading 6 is the final heading, there is no heading 7. 
- Closing tags must also match opening tags.
- Don't use multiple Heading 1 tags in the same document, there should only be one as it serves as the main heading for the web page.
- Don't skip heading levels ie, move from heading 1 to heading 3.
### Paragraphs:

Paragraphs can be opened and closed using the `<p>` tag. This will ensure that the appropriate spaces are present between paragraphs and also making it possible for people with disabilities to navigate between bodies of text on our web page using accessibility technologies like screen readers.

```html
<p>
  First paragraph. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
  do eiusmod tempor incididunt ut labore et dolore magna aliqua. Arcu cursus
  vitae congue mauris. In nisl nisi scelerisque eu ultrices vitae auctor eu
  augue. Nisi est sit amet facilisis magna.
</p>

<p>
  Second paragraph. Suscipit adipiscing bibendum est ultricies. Tortor aliquam
  nulla facilisi cras fermentum. Eget aliquet nibh praesent tristique magna. In
  hac habitasse platea dictumst vestibulum. Ornare quam viverra orci sagittis
  eu. Sit amet est placerat in.
</p>

<p>
  Third paragraph. Nisl purus in mollis nunc sed id semper risus. Ipsum a arcu
  cursus vitae congue mauris rhoncus aenean. Ridiculus mus mauris vitae
  ultricies leo integer malesuada nunc. In tellus integer feugiat scelerisque.
  Lectus mauris ultrices eros in cursus turpis massa. Sollicitudin ac orci
  phasellus egestas. Massa massa ultricies mi quis hendrerit dolor. Quam
  elementum pulvinar etiam non quam lacus suspendisse faucibus interdum. Iaculis
  nunc sed augue lacus viverra.
</p>
```

This is rendered as follows:

![](Pictures/The%20Internet%20-%20Paragaphs.png)

### Self Closing Tags:

Some tags, such as the **Horizontal Rule Element** do not have closing tags and place the forward slash before the less than operator rather than after the greater than operator:

`<hr />`

**Note:** This is also known as a *void element*.

``` html
<p>
  First paragraph. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
  do eiusmod tempor incididunt ut labore et dolore magna aliqua. Arcu cursus
  vitae congue mauris. In nisl nisi scelerisque eu ultrices vitae auctor eu
  augue. Nisi est sit amet facilisis magna.
</p>

<hr />

<p>
  Second paragraph. Suscipit adipiscing bibendum est ultricies. Tortor aliquam
  nulla facilisi cras fermentum. Eget aliquet nibh praesent tristique magna. In
  hac habitasse platea dictumst vestibulum. Ornare quam viverra orci sagittis
  eu. Sit amet est placerat in.
</p>

```

Is rendered as:

![](Pictures/The%20Internet%20-%20Horizontal%20Rule.png)

Other void elements include the *break element* `<br />`  which is used to ensure pieces of text inside a paragraph begin on a new line. By default all text inside of a paragraph will continue on one line and the web browser will wrap the text depending on the width of your browser window.

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