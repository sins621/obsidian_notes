# Introduction to React

React is a front-end library that aims to simplify the process of building web applications for the web.
## Single Page Application

React is used to create a *Single Page Application*. Instead of composing your website of different routes to access different parts of your web page we create a single page and use React to dynamically and responsively display different elements of the web-page.

A basic react application has the following file structure:

![](Pictures/React%20File%20Structure.png)

In our project we will only have a **single** html file and js file. These will serve as our entry points into our 'web-application'.

### index.html:

```html nums {9, 10}
<!DOCTYPE html>
<html lang="en">
<head>
	<title>JSX</title>
	<link rel="stylesheet" href="styles.css" />
</head>

<body>
	<div id="root"></div>
	<script src="../src/index.js" type="text/JSX"></script>
</body>
</html>
```

Our index.html file only consists of a `div` with an `id` of "root". This will serve as an entry point to our application as React will be used to render all the html relevant to our application inside of this `div`.
### index.js

```jsx nums{6-8}
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(
  <div>
    <App />
  </div>,
  document.getElementById("root")
);
```

This is the file linked to our index.html file and it serves as the entry point for our React application. You will notice that we have html inside of our js file and this is because the file is *actually* a `jsx` file. It is convention to leave it as a js file for the browser. We import React and ReactDOM and call the `render` which first expects *what* you want to render and finally *where* you would like to render it.
### App.jsx

```jsx nums {8-12}
import React from "react";

function App() {

  let greeting = "Hello World";

  return (
    <div>
      <h1>
        {greeting}
      </h1>
    </div>
  );
}

export default App;
```

The `App.jsx` file serves as the entry point to all of our React **components**. 
## Components

React helps unify the three files that are used to create webpages, html, css and js, in a single workflow by separating webpages into **components**. 

![](Pictures/React%20Components.png)

A single component is generally found in a `components` folder and will consist of a function which returns some html.

```jsx nums {9-11, 25-27, 31}
import React from "react";

function Heading() {
  const date = new Date();
  const currentTime = date.getHours();

  let greeting;

  const customStyle = {
    color: ""
  };

  if (currentTime < 12) {
    greeting = "Good Morning";
    customStyle.color = "red";
  } else if (currentTime < 18) {
    greeting = "Good Afternoon";
    customStyle.color = "green";
  } else {
    greeting = "Good Night";
    customStyle.color = "blue";
  }

  return (
    <h1 className="heading" style={customStyle}>
      {greeting}
    </h1>
  );
}

export default Heading;
```

Let's pay attention to the highlighted code segments. There's a lot to unpack from line 25 to line 27. Let's look at a few key points:

- Element attributes are pascal-cased as is the naming convention in Javascript.
- Styles can be defined as Javascript objects and passed in as objects to the style attribute. See object declaration on line 9.
- Javascript can be inserted into html using squiggly braces.

Finally on line 31 the function is exported to be imported as a module in another file, in our example it will be imported to `App.jsx`.

```jsx nums {2, 7}
import React from "react";
import Heading from "./Heading";

function App() {
  return (
    <div>
      <Heading />
    </div>
  );
}

export default App;
```

First we import our module on line 2 and finally we can see that it is used inside of our 'html' as it's **own element** with a self-closing tag.

