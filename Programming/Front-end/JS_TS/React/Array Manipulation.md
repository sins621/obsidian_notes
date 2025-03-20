# Array Manipulation

With ES6 we now have multiple different ways to manipulate Arrays in JavaScript. This will become very useful for creating dynamic websites with reusable components in React.

Some of the array methods we have access to are:

- `Map` - Which we Covered in [Mapping Components](Mapping%20Components.md)
- `Filter`
- `Reduce`
- `Find`
- `FindIndex`

## `Filter`

*Filter Creates a New Array by Keeping Items that Return True*

One confusing part of the descriptions of these methods is that they are often said to 'Create' a New Array, this implies that some form of data is *created* that can be used later however this is not the case. The reality is that these methods **return** new arrays that you will still need to store.

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

const newArray = numbers.filter((number) => {
	return number % 3 === 0;
})

console.log(newArray); // [ 3, 9, 15, 33, 36 ]
```

## `Reduce`

Reduce allows us to accumulate a single value from an array by performing an action on each element.

The `reduce` method iterates over an array and takes in 4 arguments although we will only look at the first two here. The first argument is known as the `previousValue` and the second as the `currentValue` or current value of the array at the current array index.

The `previousValue` will be the result of the previous iteration, more specifically what is *returned* from it. However, as it is not possible to have a 'previous value' on the first iteration, during the first iteration the `previousValue` will be equivalent to array at index 0 and the `currentValue` will be equivalent to array at index 1. From then on wards `previousValue` will be equivalent to the result of that prior iteration and `currentValue` will be equivalent to array at the following index and so fourth.

Say we have the same set of numbers and we simply call the method:

```javascript
const numbers = [1, 3, 4, 7, 9, 11, 15, 28, 33, 36]

numbers.reduce((accumulator, number) => {
	console.log(`Accumulator: ${accumulator}`);
	console.log(`Number: ${number}`);
	return;
})
```

```output
Accumulator: Number: 3
Accumulator: undefined
Number: 4
Accumulator: undefined
Number: 7
Accumulator: undefined
Number: 9
Accumulator: undefined
Number: 11
Accumulator: undefined
Number: 15
Accumulator: undefined
Number: 28
Accumulator: undefined
Number: 33
Accumulator: undefined
Number: 36
1
```


We can see in the example that the *`accumulator`* or `previousValue` first starts as 1, the first value in the array and the *`number`* or `currentValue` is the 2nd value in the array. Following the first iteration and every iteration there after `accumulator` is undefined and this is because we are not returning any actual value in the example.

Let's return the accumulator:

```javascript
const numbers = [1, 3, 4, 7, 9, 11, 15, 28, 33, 36]

numbers.reduce((accumulator, number) => {
	console.log(`Accumulator: ${accumulator}`);
	console.log(`Number: ${number}`);
	return accumulator;
})
```

```output
Accumulator: 1
Number: 3
Accumulator: 1
Number: 4
Accumulator: 1
Number: 7
Accumulator: 1
Number: 9
Accumulator: 1
Number: 11
Accumulator: 1
Number: 15
Accumulator: 1
Number: 28
Accumulator: 1
Number: 33
Accumulator: 1
Number: 36
```


Now we can see that, on every iteration, the value of `accumulator` is 1. This makes perfect sense as the *initial* value is one and that is also the value that is returned on every iteration. Now to use this method for an actual calculation we can sum the contents of the array:

```javascript
const numbers = [1, 3, 4, 7, 9, 11, 15, 28, 33, 36]

const sumOfNumbers = numbers.reduce((accumulator, number) => {
	console.log(`Accumulator: ${accumulator}`);
	console.log(`Number: ${number}`);
	return accumulator + number;
})

console.log(`The sum of numbers is ${sumOfNumbers}`);
```

```output
Accumulator: 1
Number: 3
Accumulator: 4
Number: 4
Accumulator: 8
Number: 7
Accumulator: 15
Number: 9
Accumulator: 24
Number: 11
Accumulator: 35
Number: 15
Accumulator: 50
Number: 28
Accumulator: 78
Number: 33
Accumulator: 111
Number: 36
The sum of numbers is 147
```


The `accumulator` holds the result of the last iteration and is used for in the calculation of the next and the final value of the `accumulator` is stored in our constant `sumOfNumbers`.

## `Find`

This method can be used to return the first occurrence in an array that matches the specified condition.

```javascript
const numbers = [1, 4, 9, 11, 15, 28, 33, 36]

const firstPrimeNumber = numbers.find((number) => {
	if (number <= 1) {
      return false; 
    }
    for (let i = 2; i <= Math.sqrt(number); i++) {
      if (number % i === 0) {
        return false; 
      }
    }
    return true;
});

console.log(firstPrimeNumber);
```

```output
11
```


