# CSS
Cascading Style Sheets
## Applying CSS to an HTML Document

CSS can be applied to websites via three methods:

- **Inline**
	`<tag style="css"/>`
- **Internal**
	`<style>css</style>`
- **External**
	`<link href="style.css"/>`
### Inline CSS

![](Pictures/CSS%20-%20Inline.png)

In this example we're changing the background color of our webpage using CSS. We add the attribute to the *html* tag with a *CSS Property*, 'background' in this case, and the value of the color blue. This method of adding CSS to an HTML document is generally not recommended but is useful if you only intend to target a single element.
### Internal CSS

![](Pictures/CSS%20-%20Internal%20CSS.png)

In this example we're using CSS tags to insert CSS code into our HTML document.
### External CSS

![](Pictures/CSS%20-%20External%20CSS.png)

Using the `<link/>` element we can link an external CSS file to our HTML file to add styling. This is the most commonly implemented method of adding CSS styling to webpages.

## CSS Selectors

Inside of our CSS file we can indicate which part of our web page we intend to add styling to by using a *selector*.
### Element Selector

Here we see the most basic form of a CSS Selector, the *element selector*:

![](Pictures/CSS%20-%20Selector.png)

In this example we're targeting the `h2` element, or header 2 element, and applying the red color to it.

**Note:** When selecting an element this way, all elements that share the same name will have styles applied to them, this is why all headings on our webpage have their colors changed to red.
### Class Selector

In this example we're we're assigning a class name to our "Red" text by using the `class` attribute. We then reference this class name in our CSS file by prefixing it with a full stop:

![](Pictures/CSS%20-%20Class%20Selector.png)

**Note:** Other elements which share the same class name will also have the same styling applied to it.
### ID Selector

In this example we're making use of the *ID Selector*. We assign an ID to an HTML element by making use of the `id` attribute and referencing this attribute in our CSS file by prefixing the name with the pound symbol.

![](Pictures/CSS%20-%20ID%20Selector.png)

While functionally it may look the same the difference between ID and Class is that ID is to be unique ie, only applied to one single element in an HTML file where as a Class is to be used to apply styling to many different elements in a single HTML file.
### Attribute Selector

In this example we are styling by attribute using the *attribute selector*.

![](Pictures/CSS%20-%20Attribute%20Selector.png)

All html elements sharing the same attribute such as `draggable`, `src`, etc, will have the styling inside square brackets and prefixed by the letter 'p' applied to them.

We can also use the attribute selector to select elements that have a specific *value* applied to the attribute that we have selected:

![](Pictures/CSS%20-%20Attribute%20Value%20Selector.png)

Here we can see that only elements which have the `draggable` attribute set to `false` have styling applied to them.
### Universal Selector

The final selector we'll look at in this document is the *universal selector*. 

```css
*{
	color:red;
{
```

Simply put, this selector applies styling to all elements inside of the HTML document.