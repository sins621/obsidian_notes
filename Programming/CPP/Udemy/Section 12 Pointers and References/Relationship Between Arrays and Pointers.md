# Introduction

- The value of an array name is the address of the first element in the array.

- The value of a pointer is an address

- If the pointer is to the same data type as the array element then the pointer and array name can be used interchangeably. (almost)

So at this point you may be wondering how we can allocate an entire array of integers and store it's address into a pointer to an integer, that's a good question and it's critical that you understand the relationship between arrays and pointers in C++.

Remember that the value of an array name is the location or the address of the first element of the array and the value of a pointer is an address. So if a pointer points to the same type of data as the array elements then the pointer and the array name are the same as far as C++ is concerned. 

The only difference is that the array name is not a variable so you can't change it, but otherwise all the calculations done to access array elements can be done with the array name or the pointer name.

```cpp nums
int scores[] {100, 95, 89};

cout << scores << endl;            // 0x61fec8
cout << *scores << endl;           // 100

int *score_ptr {scores};

cout << score_ptr << endl;         //  0x61fec8
cout << *score_ptr << endl;        // 100
```

In this example we have `scores` as array of 3 integers. If you display scores then the value of the array name is the address of the first element in the array. What if we dereference `scores`? `scores` Is an array, how do we dereference that? 

Sure, `scores` is the address of the first array element so if we go to that address, which is what dereferencing is, we get the integer. So the output statement for dereferencing scores displays 100, the first array element, now if we declare `score_ptr` as a pointer to an integer and we initialize it to `scores`, notice that the value of `score_ptr` is the same as `scores`. So when we dereference `score_ptr` we get the same results, the value of the element at that location which is 100 in this case. 

```cpp nums
int scores[] {100, 95, 89};

int *score_ptr{scores};

cout << score_ptr[0] << endl;    // 100

cout << score_ptr[1] << endl;    // 95

cout << score_ptr[2] << endl;    // 89
```

So if we pretty much use an array name and a pointer name interchangeably, that means that we should be able to use array sub-scripting on a pointer right? And that's absolutely correct, if `score_ptr` points to the first element of the scores array as it does in this example, then when we display `score_ptr[0]` we get 100. `score_ptr[1]` Is 95 and `score_ptr[2]` is 89. 

That's weird right? Well not really if you understand that C++ doesn't really have true arrays and that arrays are just the address of the first element in a chunk of memory, then this makes sense. So does that mean that we can add the offset to the pointer variable, then we can make it point to any array element? And again, yes it does, let's see how:

# Using Pointers in Expressions

We're using the same example here, notice that when we display `score_ptr` we get back an address, if we add 1 to `score_ptr` then you can see that the value of `score_ptr` has increased by 4 not by 1. Why? Because we're not adding 1 to the pointer value we're adding the **size of 1 integer** to the pointer value. The pointer doesn't hold integers, the pointer holds addresses of integers so when we add 1 we're adding the address of the next integer which is 4 bytes away, if we add 2 we're incrementing `score_ptr` by 8 which is 2 integers away.

```cpp nums
int scores[] {100, 95, 89};

int *score_ptr{scores};

cout << score_ptr << endl;           // 0x61ff10

cout << (score_ptr + 1) << endl;     // 0x61ff14

cout << (score_ptr + 2) << endl;     // 0x61ff18
```

This is the basis of pointer arithmetic which we'll talk about in the next video. Once we have `score_ptr` pointing to the integer that we want we can simply dereference the pointer to get to the integer, let's see how that works:

```cpp nums
int scores[] {100, 95, 89};

int *score_ptr{scores};

cout << *score_ptr << endl;           // 100

cout << *(score_ptr + 1) << endl;     // 95

cout << *(score_ptr + 2) << endl;     // 89
```

Here's the same example, except that we're dereferencing the expression. Notice that how we follow the pointer and display the integer that we point to. 

In this case we're moving along the array using the pointer, that's pretty cool, let's see this all together so it makes more sense. 

# Subscript and Offset Notation Equivalence

```cpp nums
int array_name[]{1,2,3,4,5};
int *pointer_name{array_name};
```

| Subscript Notation    | Offset Notation           |
| --------------------- | ------------------------- |
| `array_name[index]`   | `*(array_name + index)`   |
| `pointer_name[index]` | `*(pointer_name + index)` |

This table shows the equivalence between arrays and pointers. Notice that we can access array elements using array subscript or pointer subscript notation, using either the name of the array or the name of the pointer. You can also see that we can use array offset or pointer offset notation also, using either the array name or the pointer name.

# Examples in the IDE

```cpp nums
#include <iostream>

int main(){
    int scores[]{100, 95, 89};
    std::cout << "Value of scores: " << scores << std::endl;

    int *score_ptr{scores};
    std::cout << "Value of score_ptr: " << score_ptr << std::endl;

    std::cout << "\nArray of subscript notation -------------------" 
        << std::endl;
    std::cout << scores[0] << std::endl;
    std::cout << scores[1] << std::endl;
    std::cout << scores[2] << std::endl;

    std::cout << "\nPointer subscript notation -------------------" 
        << std::endl;
    std::cout << score_ptr[0] << std::endl;
    std::cout << score_ptr[1] << std::endl;
    std::cout << score_ptr[2] << std::endl;

    std::cout << "\nPointer offset notation -------------------" 
        << std::endl;
    std::cout << *score_ptr << std::endl;
    std::cout << *(score_ptr + 1) << std::endl;
    std::cout << *(score_ptr + 2) << std::endl;

    std::cout << "\nArray offset notation -------------------" 
        << std::endl;
    std::cout << *scores << std::endl;
    std::cout << *(scores + 1) << std::endl;
    std::cout << *(scores + 2) << std::endl;
}
```
## Output:

```
Value of scores: 0x7fffffffd8fc
Value of score_ptr: 0x7fffffffd8fc

Array of subscript notation -------------------
100
95
89

Pointer subscript notation -------------------
100
95
89

Pointer offset notation -------------------
100
95
89

Array offset notation -------------------
100
95
89
```
