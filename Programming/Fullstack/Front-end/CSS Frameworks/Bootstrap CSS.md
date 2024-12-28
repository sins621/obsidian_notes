# Bootstrap CSS

[Bootstrap](https://getbootstrap.com/) is a CSS Framework which provides us with pre-styled components and pre-defined layouts to make creating responsive and appealing web pages easier. 

We can include Bootstrap into our projects by:

- Using a *Package Manager*.
- Using a *CDN*.
## Including via CDN:

A CDN or *Content Delivery Network* is a group of geographically distributed servers that speed up the delivery of web content by bringing it closer to where users are.

We can use a CDN in this instance to include the Bootstrap CSS files into our project via link instead of actually serving the files ourselves, this way we can make use of the files in our project and when our users load our web-pages they will download the CSS files that are used from the closest server geographically to them.

Two links to the Bootstrap CDN can be found on on their [website](https://getbootstrap.com/). The *stylesheet* is provided in the `<head>` section of our web page and the script files for functionality provided by the framework must be placed at the end of our `<body>`.

```html nums {6-11,18-22}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
      crossorigin="anonymous"
    />
    <title>Test</title>
  </head>
  <body>
    <div>
      <p>Some Stuff Here</p>
    </div>
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
      crossorigin="anonymous"
    ></script>
  </body>
</html>
```
## Card Component

Let's look at the process of adding the *Card Component* to our project, we can simply navigate to the card section of the [documentations](https://getbootstrap.com/docs/5.3/getting-started/introduction/). 

![](Pictures/Bootstrap%20CSS%20-%20Card%20Component.png)

Here we can see a preview of the component and the code associated with it. Notice that styling is predominately managed by adding predefined classes to our HTML elements.

Let's add this component to our web page.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
      crossorigin="anonymous"
    />
    <title>Test</title>
  </head>
  <body>
    <div class="card" style="width: 18rem">
      <img src="flower.jpg"card-img-top" alt="..." />
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
      crossorigin="anonymous"
    ></script>
  </body>
</html>
```

![](Pictures/Bootstrap%20CSS%20-%20Card%20Example.png)

If we'd like to modify the styles provided by Bootstrap we must include our adjustments **after** when the stylesheet is inserted into our HTML file.

```html nums {12-20}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
      crossorigin="anonymous"
    />
    <style>
      /* TODO 4: Use flexbox to center the card in the vertical and horizontal center. */
      .flex-container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
      }
    </style>
    <title>Test</title>
  </head>
  <body>
    <div class="flex-container">
      <div class="card" style="width: 18rem">
        <img src="flower.jpg"card-img-top" alt="..." />
        <div class="card-body">
          <h5 class="card-title">Card title</h5>
          <p class="card-text">
            Some quick example text to build on the card title and make up the
            bulk of the card's content.
          </p>
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>
    </div>
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
      crossorigin="anonymous"
    ></script>
  </body>
</html>
```

Here we include our style **overrides** after we have included the link to Bootstrap. We can also include our own local CSS file to override the Bootstrap styling as long as it is inserted after the Bootstrap link.

Let's see the result:

![](Pictures/Bootstrap%20CSS%20-%20Example%20Styled.png)

# Bootstrap Layouts

In order to simply the layout of web pages Bootstrap utilizes a *12 Column System* whereby columns will be shifted over into the following rows if there is not enough space on screen to render them alongside one another.

![](Pictures/Bootstrap%20CSS%20-%2012%20Column%20System.png)

Let's look at an example of this behavior in code.
## Layout Code Example

```html
    <div class="container">Container
      <div class="row">Row
        <div class="col">Col 1</div>
        <div class="col">Col 2</div>
        <div class="col">Col 3</div>
        <div class="col">Col 4</div>
        <div class="col">Col 5</div>
        <div class="col">Col 6</div>
        <div class="col">Col 7</div>
        <div class="col">Col 8</div>
        <div class="col">Col 9</div>
        <div class="col">Col 10</div>
        <div class="col">Col 11</div>
        <div class="col">Col 12</div>
      </div>
    </div> 
```

I've given these elements borders to and margins to aid in visually identifying them. The container in green, row in blue and each column in red. Without including Bootstrap you see the following:

![](Pictures/Bootstrap%20CSS%20-%20Example%20No%20Bootstrap.png)

Upon resizing this web page notice no change in behavior:

![](Pictures/Bootstrap%20CSS%20-%20Example%20No%20Bootstrap%20Resize.png)

Now let's include link to the Bootstrap CDN in the `<head>`:

![](Pictures/Bootstrap%20CSS%20-%20Example%20With%20Bootstrap.png)

And let's resize the page:

![](Pictures/Bootstrap%20CSS%20-%20Example%20Bootstrap%20Resize.png)

Notice how columns are dynamically pushed over to new rows when the size is reduced. This is a result of the *Auto-Fit* behavior of Bootstrap. 