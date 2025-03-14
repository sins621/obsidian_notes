React is a front-end library that aims to simplify the process of building web applications for the web.
## Single Page Application

React is used to create a *Single Page Application*. Instead of composing your website of different routes to access different parts of your web page we create a single page and use React to dynamically and responsively display different elements of the web-page.

A basic react application has the following file structure:

![](Pictures/React%20File%20Structure.png)

In our project we will only have a **single** html file and js file. These will serve as our entry points into our 'web-application'.

## index.html:

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

**index.js**

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

**App.jsx**

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

