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

![](Pictures/How%20C%20Strings%20Stored%20in%20Memory.png)

- These characters are stored in a contagious block of memory that can be accessed as an array. 
- Notice "C++ is fun" has 10 characters but the compiler allocated 11 characters for the array because it needed space for the `null` character at the end.

## Declaring Variables:

![](Pictures/Frank%20in%20Memory.png)

- In this example we're declaring an Array and initializing it to Frank using initialize list syntax as we've been doing with integers and other types.
- Notice the C++ Compiler will allocate 6 characters to this Array since it needs to terminate the string with a `null` character.
- Notice the size of the Array is **fixed** so if you wanted to add a Y to "Frank" and create "Franky" you couldn't, without having some potential problems since the new string would not be `null` terminated.

![](Pictures/Initialize%20String%20to%208.png)

- In this example we are explicitly asking the compiler to allocate 8 characters for the character Array and we're initializing it to Frank.
- In this case it will initialize the array with "F" "r" "a" "n" "k" and the rest of the space will be zeroed out with `null` characters.
- In this case you wanted to change the character at index 5 which is that first `null` character to a lower case 'y' it would be just fine since the string now contains "Franky" and is still `null` terminated.

![](Pictures/Initialize%20without%20Data.png)

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

# Coding Exercise: Using C-Style Strings:

Using C-style Strings

In this exercise you will create a program that determines the length of a first name and last name individually and then the length of the entire name through the use of the C-style string functions `strlen`, `strcpy`, and `strcat`.

Begin by declaring and initializing the C-style string variable `first_name` to contain `"Bjarne"`.  
Now, declare and initialize a second C-style string variable `last_name` to contain `"Stroustrup"`.  
You must also declare a third C-style string variable `whole_name` but do not initialize it yet. Remember that the variable `whole_name` must be large enough to contain the first and last name with no whitespaces.  
  
Now, by using the C-style string function `strlen`, declare and initialize the variable `first_name_length` to contain the length of the `first_name` string and the variable `last_name_length` to contain the length of the `last_name` string.

  
Using the C-style string function `strcpy`, copy the `first_name` string into the `whole_name` string variable.  
Now, by using the C-style string function `strcat`, concatenate the `last_name` string at the end of the `whole_name` string.  
Finally, by using the C-style string function `strlen`, declare and initialize the variable `whole_name_length` to contain the length of the `whole_name` string.

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <iostream>
#include <cstring>
using namespace std;

void strings_and_functions() {
    
    //----WRITE YOUR CODE BELOW THIS LINE----
    
    
    
    //----WRITE YOUR CODE ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    
    cout << "The length of the first name, " << first_name 
	     << ", is " << first_name_length 
	     << " letters long and the length of the last name, " 
	     << last_name << ", is " << last_name_length 
	     << " letters long. This means that the length of the whole name              must be " << whole_name_length << " letters long.";
}
```

## My solution:

```cpp
char first_name[]{"Bjarne"};
char last_name[]{"Stroustrup"};
char whole_name[50]{"\0"};

int first_name_length = strlen(first_name);
int last_name_length = strlen(last_name);

strcat(whole_name, first_name);
strcat(whole_name, last_name);

int whole_name_length = strlen(whole_name);
```

## Instructor Solution:

```cpp
char first_name [7] {"Bjarne"};
char last_name [11] {"Stroustrup"};
char whole_name [17];

int first_name_length = strlen(first_name);
int last_name_length = strlen(last_name);

strcpy(whole_name,first_name);
strcat(whole_name,last_name);

int whole_name_length = strlen(whole_name);
```

## Takeaways:

Make sure to manually define the length of characters where it hasn't been initialized to any value yet otherwise you will encounter memory management issues and unexpected behavior in the output.