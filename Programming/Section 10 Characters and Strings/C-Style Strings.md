## Sequence of Characters

- Contiguous in Memory
- Implemented as an Array of Characters
- Terminated by a Null Character (Null)
	- null - character with a value of zero
- Referred to as Zero or Null Terminated Strings

## String Literal

- Sequence of Characters in Double Quotes, e.g. "Frank"
- Constant
- Terminated with Null Character

# How C Style Strings are Stored in Memory:

![[How C Strings Stored in Memory.png]]

- These characters are stored in a contagious block of memory that can be accessed as an array. 
- Notice "C++ is fun" has 10 characters but the compiler allocated 11 characters for the array because it needed space for the `null` character at the end.

## Declaring Variables:

![[Frank in Memory.png]]

- In this example we're declaring an Array and initializing it to Frank using initialize list syntax as we've been doing with integers and other types.
- Notice the C++ Compiler will allocate 6 characters to this Array since it needs to terminate the string with a `null` character.
- Notice the size of the Array is **fixed** so if you wanted to add a Y to "Frank" and create "Franky" you couldn't, without having some potential problems since the new string would not be `null` terminated.

![[Initialize String to 8.png]]

- In this example we are explicitly asking the compiler to allocate 8 characters for the character Array and we're initializing it to Frank.
- In this case it will initialize the array with "F" "r" "a" "n" "k" and the rest of the space will be zeroed out with `null` characters.
- In this case you wanted to change the character at index 5 which is that first `null` character to a lower case 'y' it would be just fine since the string now contains "Franky" and is still `null` terminated.

![[Initialize without Data.png]]

- In this example we ask the compiler to allocate an array of 8 characters and we don't initialize them. This could be very problematic because if you use this array as a string all C-Style string functions expect a `null` character and here there may or may not be one as we don't know what the data in the array is.
- Suppose we wanted to display the string, how are C-Style strings displayed? You start at the first element of the Array and iterate through it until reaching a `null` character but in this instance that can go on for a very long time before a `null` character is reached because it is not specified.
- You might think that C-Style strings can be initialized with the assignment operator `=` but this won't work. If we try to assign the C-Style literal "Frank" to `my_name` we get a compiler error because that's not how C-Style Strings work. Array names and literals evaluate to their location in memory so we're effectively assigning one location to another which is illegal.
- In order to assign one string to another we need to use a function called `strcpy` that copies the C-Style literal "F" "r" "a" "n" "k" to the `my_name` Array.

# Functions that work with C-Style Strings

- Copying
- Concatenation
- Comparison
- Searching
- and others

They all rely on one common factor: **That the sequence of characters they are working on is terminated with a** `null` **character.** If you are using C-Style Strings you must be vary aware of this. For Example: Suppose you have a C-Style String and you want to determine it's length, let's say we have "Frank". Since no length information is stored with the String, only the characters in the Array, the only way to determine the length is to start counting at the first Array element and then iterating until finding a `null` character.

# A few examples

```cpp
char str[80];

strcpy(str, "Hello ");   // copy
strcat (str, "there ");  // concatenate
cout << strlen (str);    // 11
strcmp (str, "Another"); // > 0

```

# `#include <cstdlib>`

General Purpose Functions

Includes functions to convert C-Style Strings to:

- integer
- float
- long
- etc.

