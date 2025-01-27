Cascading Style Sheets
# Applying CSS to an HTML Document

CSS can be applied to websites via three methods:

- **Inline**
	`<tag style="css"/>`
- **Internal**
	`<style>css</style>`
- **External**
	`<link href="style.css"/>`
## Inline CSS

![](Pictures/CSS%20-%20Inline.png)

In this example we're changing the background color of our webpage using CSS. We add the attribute to the *html* tag with a *CSS Property*, 'background' in this case, and the value of the color blue. This method of adding CSS to an HTML document is generally not recommended but is useful if you only intend to target a single element.
## Internal CSS

![](Pictures/CSS%20-%20Internal%20CSS.png)

In this example we're using CSS tags to insert CSS code into our HTML document.
## External CSS

![](Pictures/CSS%20-%20External%20CSS.png)

Using the `<link/>` element we can link an external CSS file to our HTML file to add styling. This is the most commonly implemented method of adding CSS styling to webpages.

# CSS Selectors

Inside of our CSS file we can indicate which part of our web page we intend to add styling to by using a *selector*.
## Element Selector

Here we see the most basic form of a CSS Selector, the *element selector*:

![](Pictures/CSS%20-%20Selector.png)

In this example we're targeting the `h2` element, or header 2 element, and applying the red color to it.

**Note:** When selecting an element this way, all elements that share the same name will have styles applied to them, this is why all headings on our webpage have their colors changed to red.
## Class Selector

In this example we're we're assigning a class name to our "Red" text by using the `class` attribute. We then reference this class name in our CSS file by prefixing it with a full stop:

![](Pictures/CSS%20-%20Class%20Selector.png)

**Note:** Other elements which share the same class name will also have the same styling applied to it.
## ID Selector

In this example we're making use of the *ID Selector*. We assign an ID to an HTML element by making use of the `id` attribute and referencing this attribute in our CSS file by prefixing the name with the pound symbol.

![](Pictures/CSS%20-%20ID%20Selector.png)

While functionally it may look the same the difference between ID and Class is that ID is to be unique ie, only applied to one single element in an HTML file where as a Class is to be used to apply styling to many different elements in a single HTML file.
## Attribute Selector

In this example we are styling by attribute using the *attribute selector*.

![](Pictures/CSS%20-%20Attribute%20Selector.png)

All html elements sharing the same attribute such as `draggable`, `src`, etc, will have the styling inside square brackets and prefixed by the letter 'p' applied to them.

We can also use the attribute selector to select elements that have a specific *value* applied to the attribute that we have selected:

![](Pictures/CSS%20-%20Attribute%20Value%20Selector.png)

Here we can see that only elements which have the `draggable` attribute set to `false` have styling applied to them.
# Universal Selector

The final selector we'll look at in this document is the *universal selector*. 

```css
*{
	color:red;
{
```

Simply put, this selector applies styling to all elements inside of the HTML document.

## Colors

CSS has access to many colors as of the current standard and supports a white array of *named colors* as well as colors represented by a *hex-code*

```css
  html {
	background: antiquewhite; /* named color */
  }
  h1 {
	color: whitesmoke; /* named color */
	background: darkseagreen; /* named color */
  }
  h2 {
	color: #faf8f1; /* hex color */
	background: #c58940; /* hex color */
  }
```
## Font Properties

We can use CSS to adjust various font properties such as the size, weight, family, etc.
### Size:
`font-size`

Font sizes can be described by the pixel size, point size, size relative to the parent element or size relative to the root element.

![](Pictures/Intermediate%20CSS%20-%20Sizes.png)

The **Pixel** size relates to an amount of pixels while **Point** is a unit of measurement you will commonly find in word processors. 

*em* and *rem* relative units of measurement where the unit prefixed to the unit denotes the multiple that the size of the font will be to the element it is related to. This means that for example if you were to use a font of `2em` where the element as a size of 20 pixels, the font size will be 40 pixels.

Where the two differ is that `em` is relative to any parent element such as a `<footer>` element for example, this means that if the size of the `<footer>` element changes so will our font size. `rem` However is relative to the root of the HTML page, in other words the `<html>` element.
### Weight:
`font-weight`

Font weight, which refers to how **bold** the font is, can be adjusted via keywords, relation to a parent element or a number value.

![](Pictures/Intermediate%20CSS%20-%20Font%20Weight.png)

### Family:
`font-family`

In addition to font size and weight, we can also specify the font family to be used, also known as the font face.

![](Pictures/Intermediate%20CSS%20-%20Font%20-%20Family.png)

First we specify the font that we intend to appear on screen however, not all fonts are present on every system and so we provide a *generic* fallback font that should be present on all systems.

Some generic fonts include:

- Sans Serif
- Serif
- Arial
- Cursive
- Monospace
- Fantasy
#### Font From The Web

It's also possible to include fonts from the web so that they will be sourced from the web even if the device reading the content does not have that font installed locally.

Let's look an example where we include a font from Google's font library:

![](Pictures/Intermediate%20CSS%20-%20Font%20From%20The%20Web.png)

Here we would like to include the 'Caveat' font on our web-page. We can select the 'Embed code' option which will provide us with the HTML `<link/>` elements so that we can inform the web browser where to source the fonts.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Caveat:wght@400..700&display=swap" rel="stylesheet">
```

We are also provided with the CSS code needed to access and work with this font provided by Google so that we can apply it to elements on our web-page.

```css
/* <weight>: Use a value from 400 to 700 */

.caveat-<uniquifier> {
  font-family: "Caveat", cursive;
  font-optical-sizing: auto;
  font-weight: <weight>;
  font-style: normal;
}
```
### Text Alignment
`text-align`

We can also specify where text should be aligned on screen such is at the `left` point, `center` or the `right` point.
# CSS Box Model

CSS Handles HTML elements by surrounding them with a 'box' and providing us with the tools needed to modify elements of this box.

![](Pictures/Intermediate%20CSS%20-%20Box%20Model.png)

Many developer tools in web browser's will use this diagram to display the box-model implemented by CSS. The properties of the box model that we can modify are:

- **Padding**
- **Border**
- **Margin**
## Padding
`padding`

The padding effects the spacing between our element and it's border. Say we have an element with a paragraph of text inside of it where the border is a white solid line and the background color is blue:

![](Pictures/Intermediate%20CSS%20-%20No%20Padding.png)

Now let's add padding to this element, say 10 pixels:

![](Pictures/Intermediate%20CSS%20-%20Padding.png)

The border is pushed away from the paragraph but also notice that the entire object has now become larger.
## Border
`border`

We can add a border around our objects with varying sizes, remember this will be placed after the padding.g

![](Pictures/Intermediate%20CSS%20-%20Border.png)

We can use these three attributes to control the:

- Width in pixels.
- Type such as solid or dashed.
- Color by keyword,  or hexadecimal.

If we would like to make an adjustment to one of the *sides* of our border we an add that adjustment **after** we initially created the border:

```css
border: 20px solid black;
border-top: 0px;
```

Here we can see that the top of the border has now been set to 0 pixels.

![400](Pictures/Intermediate%20CSS%20-%20Border%20Top.png)

We can also adjust each side by adjusting the `border-width` property. This property can take up to 4 arguments in order separated by spaces  where each argument adjusts the faces starting from the top and moving clockwise:

```css
border: 20px solid black;
border-width: 20px 10px 5px 0px
/*            ^1   ^2   ^3  ^4           /*
```

![](Pictures/Intermediate%20CSS%20-%20Border%20-%20Width.png)

If we provide only two values as arguments to the `border-width` then the first argument will adjust the size of the top/bottom borders and the second argument the right/left borders.
## Margin
`margin`

Margin is responsible for the spacing **between** elements. Say we duplicate our paragraph element from earlier:

![](Pictures/Intermediate%20CSS%20-%20No%20Margin.png)

Now let's add a margin of 10 pixels:

![](Pictures/Intermediate%20CSS%20-%20Margin.png)

Now we can see that there is a gap between these two elements however do note that both of these elements are being styled by the same rules meaning that they **both have a margin of 10 pixels**. This means that the gap between them is effectively 20 pixels.
## Divisions
`<div></div>`

We can place multiple elements inside a single 'box-model' by using the division tag, this way we can apply the same adjustments to padding, margins and apply a border to all elements as a whole that are inside of this division.

![](Pictures/Intermediate%20CSS%20-%20Division.png)

In this image I've placed both of our paragraphs inside of a division and given it a solid red border with a width of 10 pixels. Notice that the margin is still present between these paragraphs and they retain their borders.

# The Cascade

The reason CSS is called **Cascading Style Sheets** is because elements are styled in an order of importance from beginning to end and the order can be mentally visualized as a water cascade.

![](Pictures/CSS%20-%20Cascade.png)

## Order of Importance

In order to determine which styling takes precedent if the same attributes are being modified among them CSS employs the following order of importance:

1. Position
2. Specificity
3. Type
4. Importance
### Position

The first thing that is looked at is the position of one rule to the next ordered from top to bottom.

![](Pictures/CSS%20-%20Position%20Example.png)

Because the rule to color the list item to blue is below to the rule to color it to red the text will be colored *blue*.

The same is true for the **overall order of importance**. In other words *Type* will take precedence over *Specificity* because it is lower in the order.
### Specificity

Specificity refers to how specific a selector is in terms of the elements that you're applying the CSS Rules to.

The order of specificity is as follows:

1. Element Selector
2. Class Selector
3. Attribute Selector
4. ID Selector

```html
<li id="first-id" class="first-class" draggable>
```

```css
li {
  color: blue;
}

.first-class {
  color: red;
}

li[draggable] {
  color: purple;
}

#first-id {
  color: orange;
}
```

In this example the list item will be *orange* because ID is last in our order of specificity.
### Type

Type refers to the type of styling that is being applied. As we have learnt at the beginning of this document we can apply styling *Inline*, *Internally* and *Externally*. The order of precedence for the type of styling however is as follows:

1. Externally
2. Internally
3. Inline

```html
<link rel="stylesheet" href="./style.css">
<style> </style>
<h1 style=" ">Hello</h1>
```

In this example the styling that will be applied is the *Inline* styling because it is last in the order of precedence for Type.
### Importance

The `!important;` keyword ensures that whatever rule it is placed by will always be the most important rule and will be processed.

```css
color: red;
color: green !important;
```

Therefore, in this example the element will be styled green.

## Combining CSS Selectors

HTML Files can grow quite large with many different hierarchies and nested elements. We can combine CSS Selectors in order to target specific elements that may otherwise have require adding unique IDs.

```html nums {1,3}
<p> Yellow Text</p>
<div class="box inner-box">
	<p>White Text</p>
</div>
```

```css nums
p {
  color: yellow;
}
.inner-box p {
  color: white;
}
```

In this example our paragraph tag containing "White Text" will be styled white while other paragraph tags in our document will be styled yellow. By combining the class name `inner-box` and the element on line 4 of our CSS snippet we can target specifically the paragraph tag nested inside an element with thjat specific class.

There are multiple ways of combining CSS Selectors that all select html elements in different ways. 

They are as follows:

- **Group**
- **Child**
- **Descendant**
- **Chaining**
### Group
`
The group selector, used by separating items by commas, allows you to apply your CSS Rule to multiple elements at once.

```CSS
h1, h2{
  color: green;
}
```

### Descendant

Descendants of elements can be selecting by including the element after the parent separated by a space.

```css
ancestor descendant {
  color: blue;
}
```

This means that no matter how deep the element is nested, as long as it has the specified ancestor it will be styled by this rule.

```html
<ancestor>
	<some_element>
		<some_other_element>
			<descendant>Blue Text</descendant>
		</some_other_element>
	</some_element>
</ancestor>
```

### Child

By using a greater than sign `>` we can select an element that is a child of another element. This means that the item needs to be **directly** nested from the parent.

```html
<parent>
	<child>Affected Item</child>
</parent>
```

```css
parent > child {
  color: firebrick;
}
```

**Note**: If the element is nested more than one element deep from the parent than it is not selectable in this manner.
## Chaining

When we combine selectors by chaining we are asking for the style to be applied when *ALL* selectors are true. In order to use this kind of selection we need to add selectors together with no spaces.

```css
selector1selector2{
  color: seagreen;
}
```

The intention here is to chain together multiple identifiers for example say we had an HTML element as follows:

```html
<h1 id="title" class="big heading">Hello World</h1>
```

We can be very specific when selecting this element by chaining all of it's identifiers together.

```css
h1#title.big.heading {
  color: yellow;
}
```

**Note**: Because classes and IDs have prefixes while elements don't it's important to begin your chain with the name of the element you are targeting before adding other identifiers.
## Combining Combiners

It is possible to combine combiners together for added granularity:

```css
ancestor descendant#id.class{
  font-size: 2rem;
}
```

# Managing Layout

The web has adopted a "responsive-design" approach to creating web-pages. If you're like me you may have mistook the usage of "responsive" to imply that the web-page responds quickly to user interaction but the term is actually used to create an interface or layout that responds to the *environment* it is being placed in.

In other words, the expectation these days is that web-pages are built to scale efficiently between different platforms, screen sizes and input methods. We will use various tools such as media queries, grid layout and flex-boxes to achieve this responsive goal.
## CSS Positioning

The `position` attribute dictates the positioning behavior of the HTML element as well as how it is effected by other positioning attributes such as `left` and `top`.

There are 4 positioning modes that can be chosen:

- Static
- Relative
- Absolute
- Fixed
### Static Positioning

This is the default positioning mode. The element will be placed in the natural HTML flow after the element that has been placed before it.

**Note**: `left` and `top` don't effect the positioning of the HTML element when this mode is selected.

![](Pictures/CSS%20-%20Static%20Positioning.png)

### Relative Positioning

This option positions the element relative to it's original or static position.

![](Pictures/CSS%20-%20Relative%20Position.png)

### Absolute Positioning

The item is positioned relative to the nearest *positioned* ancestor *or* top left corner of the webpage.

![](Pictures/CSS%20-%20Absolute%20Positioned.png)

In this example the Ancestor div has it's position set to an option other than static and so our div is positioned relative to it because it is it's nearest ancestor. However, if there is no ancestor with it's position manually set the following will occur:

![](Pictures/CSS%20-%20Absolute%20No%20Ancestor.png)

The div is moved to the top left of the web page.
### Fixed Position

With this option the element will be placed in a fixed position relative to the browser window and will *ignore* scrolling and always stay where it is placed.

![](Pictures/CSS%20-%20Fixed%20Positioning.png)

### Z-Index

![](Pictures/CSS%20-%20Z-Index.png)

Elements have a Z-Index or a position on the Z Axis. This basically determines which element is shown on top of another. If the Z-Index of one element is higher than another then it will be placed on top of that element. This can by modified by adjusting the `z-index` property.
## Display

What's the difference between a `<div>` and a `<span>`? Functionally, `<div>` has the **Display** setting of *block* and `<span>` has the setting *inline*. This effects how the browser displays HTML elements following one another.

Say we have two headings:

![](Pictures/CSS%20-%20Headings.png)

**Note**: In order to showcase the differences between display settings the height has been set to `200px` for both headings.

By default the property of an `h1` is *block*.  When the block setting is used each HTML element will be placed on to a new line. Let's change the display setting to *inline*.

![](Pictures/CSS%20-%20Headers%20Inline.png)

Now we can see that the HTML elements are placed on the same line if there is space, if there is no room available to fit all inline elements than elements that would be cropped off will pass on to the next line.

You may have noticed that the *height* property has changed. This is because the *inline* display setting ignores the not only the *height* property but also the *width* property. We can however maintain control of the width and height of the element while keeping our elements inline by setting the display property to *inline-block*.

![](Pictures/CSS%20-%20Headings%20Inline%20Block.png)

Now we can see that we have inline behavior while maintaining control over the *height* and *width* properties.

```css
h1 {
  color: white;
  background: blue;
  display: inline-block;
  height: 200px;
  width: 200px;
} 
```
## Float

The layout of the web-page borrows many ideas from print media. Information is presented hierarchically, using a variety of heading sizes, dedicated paragraphs for specific contexts, and emphasized elements such as bold or italicized text. The design incorporates a grid-based structure that organizes content into columns and sections, ensuring both visual consistency and readability.

In the example below we can see how text *wraps* around the image of the car. We can use the **float** property to *float* an item to the right or left so that text is able to wrap around it.

![](Pictures/CSS%20-%20Newspaper.png)

Let's compare the following HTML with and without `float: left;` applied:

```html
<h2>CatCSS</h2>

<img src="cat.jpeg" alt="cat in a box" />
<p class="first-paragraph">Nap all day cat dog hate mouse eat string barf pillow no baths hate everything but kitty poochy. Sleep on keyboard toy mouse squeak roll over. Mesmerizing birds. Poop on grasses licks paws destroy couch intently sniff hand. The dog smells bad gnaw.</p>
```

![](Pictures/CSS%20-%20Float%20Left.png)

**Note**: When applying the float property to larger sections it may have unintended results with other elements, for example if we also happen to have a `<footer>` it may improperly wrap besides the image if there is room.

![](Pictures/CSS%20-%20Footer%20Wrapping.png)

In order to avoid this we will need to change the *float* property on the `<footer>` to **'clear'**.

![](Pictures/CSS%20-%20Float%20Clear.png)



## Media Query

Media Query allows you to set rules that need to be met in order for CSS inside the Media Query block to be executed.

For instance we can set a minimum pixel size for a rule to be executed:

```css
@media(min-width: {your-min-width}px){
	{foo}:bar;
}
```

This way when the display is equal to or above this minimum `foo` will be applied.

![](Pictures/CSS%20-%20Media%20Query%20Rule.png)

We can also set a *maximum* width as well as applying both rules at the same time.

```css
@media(max-width: {your-max-width}px){
	{foo}:bar;
}

@media(max-width: {your-max-width}px) and (max-width: {your-max-width}px){
	{foo}:bar;
}
```

There are also context specific Media Queries that you might see such as `@media screen(orientation=landscape){}` to enable to you have separate rules for if the web-page was to be displayed on a screen or `@media print(){}` to be printed however that is quite rare these days.
