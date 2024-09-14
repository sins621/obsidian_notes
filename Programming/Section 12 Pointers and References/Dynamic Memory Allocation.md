# Introduction

## Allocating Storage from the Heap at Runtime

Need a refresher on the [Heap](https://youtu.be/wJ1L2nSIV1s?si=c3l4UNGZ3Knw48fI)?

- We Often Don't Know How Much Storage We Need Until We Need It

- We Can Allocate Storage For a Variable At Run Time

- Recall C++ Arrays

	- We Had To Explicitly Provide The Size And It Was Fixed'

	- But Vectors Grow And Shrink Dynamically

- We Can Use Pointers To Access Newly Allocated Heap Storage

Let's talk about one of the main use cases for pointers, that is dynamic memory allocation. When we're developing software we often have no idea how much storage we're going to need to model our data. For example if we're modelling the students in our class, how many students do we allocate the storage for? If we're using an Array to model the students then we need to know exactly how many students we have, since once we allocate an array it's fixed in size. 

I know what you thinking, didn't we agree earlier that we should be using vectors instead of arrays? Yes we did, and that's still true, however it's important to understand how to allocate memory dynamically, not just for arrays but for other data including objects.

Also how do you think vectors work behind the scenes? They use techniques to allocate and de-allocate memory from the heap so we really need to understand how that works. 

In this lesson we'll go over the basics of allocating memory dynamically from the heap. All memory that's allocated dynamically via a pointer comes from the heap or the free store. As I said we'll use dynamic memory allocation again later in this course in the context of object orientated objects.

So how do we allocate storage at run-time? Let's see:

# Using `new` to allocate storage

We use the `new` keyword to allocate storage at run-time. In this example we declare `int_ptr` as a pointer to an integer. Rather than assigning the address of some integer variable as we've done previously, why don't we create an integer at run-time that's on the heap and store that variable's address in `int_ptr`.

That's pretty cool, you can see how easy it is, `int_ptr` equals `new int`, that's it, that's all it takes. This allocates storage for an integer on the heap and stores it's address in `int_pointer`. Now we can use the pointer to access the integer.

```cpp nums
int *int_ptr{nullptr};

int_ptr = new int;                   // allocate an integer on the heap

cout << int_ptr << endl;             // 0x2747f28

cout << *int_ptr << endl;            // 41188048 - garbage

*int_ptr = 100;

cout << *int_ptr << endl;            // 100
```

The first output statement displays the value of `int_ptr`, this is the address of the newly created integer. If we want to get to that integer we need to dereference the pointer, but notice what get's displayed. A really large integer value, that's because the integer that was allocated hasn't been initialized yet and it contains garbage data.

So in order to assign a value to that integer on the heap, we dereference the pointer to get to the integer and then store 100 in it in this case. Now when we display the value of the integer we get back 100. 

A couple of things to understand; when you allocate storage in this manner the storage is on the heap, the allocated storage contains garbage data until you initialize it. The allocated storage does not have a name, the only way to get to to that storage is via the pointer. If you lose the pointer because it goes out of scope, or you reassign it then you lost your only way to get to that storage and you have a memory leak. 

Finally, when you're done using the storage then you must de-allocate the storage so that it's again available to the rest of the program. Let's see how:

# Using `delete` to De-Allocate Storage

Here we can see that we again `int_ptr` as a pointer to an integer, then we assign `new int` to `int_ptr`. This statement allocates storage for an integer on the heap and stores the address of that integer in `int_ptr` just like before. 

```cpp nums
int *int_ptr{nullptr};

int_ptr = new int;      // allocate an integer on the heap

. . .

delete int_ptr;         // frees the allocated storage
```

We can use the pointer as we wish and then when we're done we need to release or de-allocate the storage that we allocated for that integer. We can do that easily by using the `delete` keyword followed by the name of the pointer. 

Make sure that the address in the pointer is an address of storage that was allocated using `new`.

# Using `new[]` to allocate storage for an array

We just saw an example of allocating a single integer dynamically, you can do the same with doubles, strings, vectors and so fourth. But in this example we'll do something a little more useful than allocating a single integer.

How about we allocate an entire array of integers on the heap at runtime? 

```cpp nums
int *array_ptr {nullptr};
int size{};

cout << "How big do you want the array? ";
cin >> size;

array_ptr = new int[size];         // allocate array on the heap

// We can access the array here
// We'll see how in a few paragraphs
```

In the sample code we declare a pointer to an integer called `array_ptr` and integer named integer named `size`. We ask the user how big they want the array to be, this could be the number of scores on an exam or the number of temperatures to read and so fourth. Then we use the `new` operator with [] brackets this time and the number of elements to allocate inside the brackets.

This will attempt to allocate that many integers on the heap contiguously in memory, if the storage is successfuly created then the address of the first integer is stored in `array_ptr`. That's pretty easy. Of course when we're done with the memory we need to release it de-allocate it, let's see the syntax for that.

# Using `delete[]` to De-Allocate Storage For An Array

Here's the same code example but the last statement deletes the entire array that we allocated dynamically, notice the [] brackets between the `delete` and name of the pointer. These brackets must be empty, do not include anything inside these brackets.

 ```cpp nums
int *array_ptr {nullptr};
int size{};

cout << "How big do you want the array? ";
cin >> size;

array_ptr = new int[size];         // allocate array on the heap
. . .

delete [] array_ptr;               // free allocated storage
```

Let's go to the IDE and create some storage dynamically:
# Examples In The IDE