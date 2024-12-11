# Intermediate CSS

In this document we'll explore some more intermediate CSS topics.
### Colors

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
### Font Properties

We can use CSS to adjust various font properties such as the size, weight, family, etc.
#### Size:
`font-size`

Font sizes can be described by the pixel size, point size, size relative to the parent element or size relative to the root element.

![](Pictures/Intermediate%20CSS%20-%20Sizes.png)

The **Pixel** size relates to an amount of pixels while **Point** is a unit of measurement you will commonly find in word processors. 

*em* and *rem* relative units of measurement where the unit prefixed to the unit denotes the multiple that the size of the font will be to the element it is related to. This means that for example if you were to use a font of `2em` where the element as a size of 20 pixels, the font size will be 40 pixels.

Where the two differ is that `em` is relative to any parent element such as a `<footer>` element for example, this means that if the size of the `<footer>` element changes so will our font size. `rem` However is relative to the root of the HTML page, in other words the `<html>` element.
#### Weight:
`font-weight`

Font weight, which refers to how **bold** the font is, can be adjusted via keywords, relation to a parent element or a number value.

![](Pictures/Intermediate%20CSS%20-%20Font%20Weight.png)

#### Family:
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
##### Font From The Web

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
#### Text Alignment
`text-align`

We can also specify where text should be aligned on screen such is at the `left` point, `center` or the `right` point.
## CSS Box Model

CSS Handles HTML elements by surrounding them with a 'box' and providing us with the tools needed to modify elements of this box.

![](Pictures/Intermediate%20CSS%20-%20Box%20Model.png)

Many developer tools in web browser's will use this diagram to display the box-model implemented by CSS. The properties of the box model that we can modify are:

- **Padding**
- **Border**
- **Margin**
### Padding
`padding`

The padding effects the spacing between our element and it's border. Say we have an element with a paragraph of text inside of it where the border is a white solid line and the background color is blue:

![](Pictures/Intermediate%20CSS%20-%20No%20Padding.png)

Now let's add padding to this element, say 10 pixels:

![](Pictures/Intermediate%20CSS%20-%20Padding.png)

The border is pushed away from the paragraph but also notice that the entire object has now become larger.
### Border:
`border`

We can add a border around our objects with varying sizes, remember this will be placed after the padding.

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
### Margin
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