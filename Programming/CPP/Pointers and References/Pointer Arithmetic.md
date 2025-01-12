# Introduction

- Pointers Can Be Used In:

	- Assignment Expressions
	
	- Arithmetic Expressions
	
	- Comparison Expressions

- C++ Allows Pointer Arithmetic

- Pointer Arithmetic Only Makes Sense With Raw Arrays

# Increment & Decrement Operators

Let's start by looking at the increment and decrement operators in the context of pointers. The increment operator increments the address stored in a pointer variable so that it points to the next element in contiguous memory. 

 - (++) increments a pointer to point to the next array element.

	`int_ptr++;`

So, if `int_ptr` is currently pointing to address 1000 then `int_ptr++` will increment the address it's pointing to by the size of the data type it's pointing to which in this case is an integer. That's 4 on most machines meaning `int_ptr` will now point to 1004. In the case of a double it would be larger. 

If the pointer is pointing to the address of a very large data type then the increment operator would increment it by whatever the size of that large data type is.

 - (--) decrements a pointer to point to the previous array element.

	`int_ptr--;`

The decrement operator works exactly the same way except that it decrements the value stored in the pointer variable.  

# Addition and Subtraction Operators
We can also use the addition and subtraction operators with pointers.

The addition operator determines the operand on the right hand side of the expression and multiplies that number by the size of the element and that's what's being added to the pointer.

- (+) increment pointer by `n * sizeof(type)`

	`int_ptr += n; or int_ptr = int_ptr + n

So adding two to the integer pointer increments the pointer by two times the size of an integer. Naturally pointer arithmetic is machine specific since the size of C++ types vary from machine to machine.

The subtraction operator works in the same way, except that we're decrementing the pointer's value.

- (-) decrement pointer by `n * sizeof(type)`

	`int_ptr -= n; or int_ptr = int_ptr - n

## Subtracting Two Pointers

- Determine The Number Of Elements Between The Pointers

- Both Pointers Must Point To The Same Data Type

	`int n = int_ptr2 - int_ptr1;`

What do you think is the result of subtracting one pointer from another? If both pointers point to the same data type then the result will be the number of elements between the two pointers, however if the pointers point to different data types then you'll be presented with a compiler error.

Finally let's see how we can compare pointers.
# Comparing Two Pointers `==` and `!=`

Determine If Two Pointers Point To The Same Location

- does NOT compare the data where they point!

We can compare pointers with the equality operators. If we want to compare two pointers we can simply compare them using the equal or not equal operators but be aware that this will compare the values of the pointer variables so if the pointers are pointing the same address then they are considered equal, otherwise they are considered not equal.

The data that they're pointing to is not considered when checking equality. 

The sample code shows an example of comparing pointers:

```cpp nums
string s1 {"Frank"};
string s2 {"Frank"};

string *ps1 {&s1};
string *ps2 {&s2};
string *ps3 {&s1};

cout << (p1 == p2) << endl;    // false
cout << (p1 == p3) << endl;    // true
```

In this example `p1` and `p2` point to different addresses and `p1` and `p3` point to the same addresses. You can see that if we compare `p1` and `p2` false is returned and if we compare `p1` and `p3` true is returned because they point towards the same address. 

All three pointers point to strings with the value "Frank" but that's not considered when you want to compare pointers. 

So how do you compare what the pointers are pointing to? Simple, just follow the pointers, dereference them, and compare what they're pointing to. Let's look at an example:

```cpp nums
string s1 {"Frank"};
string s2 {"Frank"};

string *ps1 {&s1};
string *ps2 {&s2};
string *ps3 {&s1};

cout << (*p1 == *p2) << endl;    // true
cout << (*p1 == *p3) << endl;    // true
```

Here we have the same example except that we're dereferencing the pointers before comparing them. So in this case `p1` and `p2` point to different strings but those strings both happen to be "Frank" so this will display true. `p1` And `p3` point to the same string so this will also be true.

That's an intro to pointer arithmetic, let's head over to the IDE and see some more examples.