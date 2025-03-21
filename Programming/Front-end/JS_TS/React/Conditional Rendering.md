# Conditional Rendering

We can use `bool` based logic to conditionally render components in React.

For example let's say if it's a sunny day we want to display an `<h1>` that says to wear sunscreen and if it's not then we'll tell the user to wear a jersey.

```jsx
import React from "react";

const isSunnyDay = true;

function App() {
  return (
    <div>
    {
    if (isSunnyDay) {
	    <h1>Wear Sunscreen</h1>
    } else {
	    <h1>Bring a Jersey</h1>
    }
    }
    </div>
  );
}

export default App;
```

Now this will **not** work because an expression is expected here, this code doesn't return a value and as a result can't be evaluated to display the headings.

However, we can use an expression to achieve this result by using the *ternary operator* `?`.

## Ternary Operator

The ternary operator allows us to evaluate a condition and execute code depending on the result, the code is structured as follows:

`CONDITION ? EXECUTION IF TRUE : EXECUTION IF FALSE`

Applying that to just the `App` function of our example:

```jsx
function App() {
  return (
    <div>
    {isSunnyDay ? <h1>Wear Sunscreen</h1> : <h1>Bring a Jersey</h1>}
    </div>
  );
}
```

This code is render-able and because it is react it will update in real-time based on the value of the bool.

If all we need to do is display something if a value is true and *not* display it if a value is false then we can use *Short-circuit evaluation*.

## Short-circuit evaluation

The 'logical AND' operator `&&` works in a very unique way in JavaScript.

Generally speaking the `&&` operator is used when when evaluating conditions, specifically specifying that both conditions need to be true in order for some code to execute.

When evaluating code using the `&&` operator in JavaScript the **2nd** condition will not be evaluated if the **1st** condition is falsey. Another quirk of JavaScript is that if this operator is not used inside a conditional statement such as an `if` statement then the code following the `&&` operator will be executed if the 1st value is not falsey.

```javascript
const isSunnyDay = true;

console.log(isSunnyDay && "Bring Sunscreen");

// Output: Bring Sunscreen
```

This is *unique* to JavaScript. Attempting to do a similar thing in C++ will result in a compiler error if the condition is not enclosed in brackets and if it is enclosed in brackets then it will return a bit value, 0 or 1.

We can use this behavior to conditionally render HTML elements and components in React.

```jsx
import React from "react";

let isSunnyDay = true;

function App() {
  return <div> {isSunnyDay && <h1>Bring Sunscreen</h1>}</div>;
}

export default App;
```

This works as you expect, the header is rendered when the value is true, or 'not falsey', and will not be rendered if the 1st value is indeed falsey.