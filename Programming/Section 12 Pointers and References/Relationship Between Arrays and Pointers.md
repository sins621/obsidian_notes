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

In this example we have `scores` as array of 3 integers. If you display scores then the value of the array name is the address of the first element in the array.