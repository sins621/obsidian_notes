# React Props

React properties or 'Props' allow us to create usable components by making information on these components modifiable when it is reused.

Say we have the following code:

```jsx
import React from "react";
import ReactDOM from "react-dom";

ReactDOM.render(
  <div>
    <h1>My Contacts</h1>

    <h2>Beyonce</h2>
    <img
      src="https://blackhistorywall.files.wordpress.com
      /2010/02/picture-device-independent-bitmap-119.jpg"
      alt="avatar_img"
    />
    <p>+123 456 789</p>
    <p>b@beyonce.com</p>

    <h2>Jack Bauer</h2>
    <img
      src="https://pbs.twimg.com/profile_images/
      625247595825246208/X3XLea04_400x400.jpg"
      alt="avatar_img"
    />
    <p>+987 654 321</p>
    <p>jack@nowhere.com</p>

    <h2>Chuck Norris</h2>
    <img
      src="https://i.pinimg.com/originals/e3/94/4
      7/e39447de921955826b1e498ccf9a39af.png"
      alt="avatar_img"
    />
    <p>+918 372 574</p>
    <p>gmail@chucknorris.com</p>
  </div>,
  document.getElementById("root")
);
```

Here we can see that the following pattern is repeated 3 times:

```jsx
<h2>Beyonce</h2>
<img
  src="https://blackhistorywall.files.wordpress.com
  /2010/02/picture-device-independent-bitmap-119.jpg"
  alt="avatar_img"
/>
<p>+123 456 789</p>
<p>b@beyonce.com</p>
```

While this wouldn't take too long to create for a small example like this, for larger projects it'd be great if we could create a reusable component from this pattern and only modify the information inside of the tags. We can do this using React properties:

```jsx
function Card(prop) {
  return (
    <div>
      <h2>{prop.name}</h2>
      <img src={prop.img} alt="avatar_img" />
      <p>{prop.tel}</p>
      <p>{prop.email}</p>
    </div>
  );
}
```

We already know that if we want to create a reusable component all we need to do is create a function that returns some html. However, it is possible to pass information to this component as we would any function, via the function body brackets.

`prop` Becomes a JavaScript object that carries information that is passed into it the same way you would pass attributes into an html element:

```jsx nums {3-9}
ReactDom.render(
	<div>
		<Card
		  name="Beyonce"
		  img="https://blackhistorywall.files.wordpress.com
		  /2010/02/picture-device-independent-bitmap-119.jpg"
		  tel="+123 456 789"
		  email="b@beyonce.com"
		/>
	</div>,
	document.getElementById("root")
);
```

This produces the following JavaScript object:

```javascript
props = {
	name:"Beyonce",
	img:"https://blackhistorywall.files.wordpress.com/2010/02/picture-device-independent-bitmap-119.jpg",
	tel:"+123 456 789",
	email:"b@beyonce.com"
}
```

Now the component can be reused with different values for each instance:

```jsx
import React from "react";
import ReactDOM from "react-dom";

function Card(prop) {
  return (
    <div>
      <h2>{prop.name}</h2>
      <img src={prop.img} alt="avatar_img" />
      <p>{prop.tel}</p>
      <p>{prop.email}</p>
    </div>
  );
}

ReactDOM.render(
  <div>
    <h1>My Contacts</h1>
    <Card
      name="Beyonce"
      img="https://blackhistorywall.files.wordpress.com
      /2010/02/picture-device-independent-bitmap-119.jpg"
      tel="+123 456 789"
      email="b@beyonce.com"
    />

    <Card
      name="Jack Bauer"
      img="https://pbs.twimg.com/profile_images/625247595825246208/
      X3XLea04_400x400.jpg"
      tel="+987 654 321"
      email="jack@nowhere.com"
    />

    <Card
      name="Chuck Norris"
      img="https://i.pinimg.com/originals/e3/94/47/e39447
      de921955826b1e498ccf9a39af.png"
      tel="+918 372 574"
      email="gmail@chucknorris.com"
    />
  </div>,
  document.getElementById("root")
);
```