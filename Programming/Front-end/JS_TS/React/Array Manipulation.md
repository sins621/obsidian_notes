# Array Manipulation

With ES6 we now have multiple different ways to manipulate Arrays in JavaScript. This will become very useful for creating dynamic websites with reusable components in React.

Some of the functions we have access to are:

- `Map` - Which we Covered in [Mapping Components](Mapping%20Components.md)
- `Filter`
- `Reduce`
- `Find`
- `FindIndex`

## `Filter`

*Filter Creates a New Array by Keeping Items that Return True*

One confusing part of the descriptions of these functions is that they are often said to 'Create' a New Array, this implies that some form of data is *created* that can be used later however this is not the case. The reality is that these functions **return** new arrays that you will still need to store.

Let's say we have an array of numbers and we want to create a new list comprised only of numbers divisible by 3. We could loop over them with `forEach()` and then push elements that match our condition into a new array.

```javascript
const numbers = [1, 3, 4, 7, 9, 11, 15, 28, 33, 36]
let newArray = []

numbers.forEach((number) => {
	if (number % 3 === 0) newArray.push(number);
})

console.log(newArray); // [ 3, 9, 15, 33, 36 ]
```

While perfectly suitable we can reduce the two step process of *1. Creating the New Array* and *2. Adding Items to The New Array* to a 'single' operation.

```javascript
const numbers = [1, 3, 4, 7, 9, 11, 15, 28, 33, 36]

let newArray = numbers.filter((number) => {
	return number % 3 === 0;
})

console.log(newArray); // [ 3, 9, 15, 33, 36 ]
```

