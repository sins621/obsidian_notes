# Mapping Components

Part of the usefulness of reusable components is the ability to reduce repetition in our code when we'd like to display multiple of the same component. In [React Props](React%20Props.md) we created a reusable 'card' component however we as you can see in that example we are repeating the card three times:

```jsx
function App() {
  return (
    <div>
      <h1 className="heading">My Contacts</h1>

      <Card
        name={contacts[0].name}
        img={contacts[0].imgURL}
        tel={contacts[0].phone}
        email={contacts[0].email}
      />
      <Card
        name={contacts[1].name}
        img={contacts[1].imgURL}
        tel={contacts[1].phone}
        email={contacts[1].email}
      />
      <Card
        name={contacts[2].name}
        img={contacts[2].imgURL}
        tel={contacts[2].phone}
        email={contacts[2].email}
      />
    </div>
  );
}
```

The only difference here is that we are grabbing the data from a contacts file which contains the following list:

```JavaScript
const contacts = [
  {
    id: 1,
    name: "Beyonce",
    imgURL:
      "https://blackhistorywall.files.wordpress.com/2010/02/picture-device-independent-bitmap-119.jpg",
    phone: "+123 456 789",
    email: "b@beyonce.com"
  },
  {
    id: 2,
    name: "Jack Bauer",
    imgURL:
      "https://pbs.twimg.com/profile_images/625247595825246208/X3XLea04_400x400.jpg",
    phone: "+987 654 321",
    email: "jack@nowhere.com"
  },
  {
    id: 3,
    name: "Chuck Norris",
    imgURL:
      "https://i.pinimg.com/originals/e3/94/47/e39447de921955826b1e498ccf9a39af.png",
    phone: "+918 372 574",
    email: "gmail@chucknorris.com"
  }
];

export default contacts;
```

Instead of manually adding a component for every entry we can use the JavaScript `map()` function.

*"`map()` creates a new array from calling a function for every array element."* -[w3schools](https://www.w3schools.com/jsref/jsref_map.asp)

So let's create a function that serves to create card components from a given contact:

```jsx
function createCart(contact) {
  return (
    <Card
      key={contact.id}
      name={contact.name}
      img={contact.imgURL}
      tel={contact.phone}
      email={contact.email}
    />
  );
}
```

**Note**: Failing to provide a unique key for the component when creating multiple of the same kind will result in a warning from the [React Dev Tools](https://chromewebstore.google.com/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) as the key is used internally by React.

In order to use our function inside of our code we simply need to call it inside squiggly braces:

```jsx nums {5}
function App() {
  return (
    <div>
      <h1 className="heading">My Contacts</h1>
      {contacts.map(createCart)}
    </div>
  );
}
```

