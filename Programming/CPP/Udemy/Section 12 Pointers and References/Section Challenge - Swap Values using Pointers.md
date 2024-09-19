# Specification:

Write a C++ function `swap_pointers` that takes two integer pointers as input and swaps the values that they are pointing to.  You can use a temporary variable if you wish but try to do it without using any temporary variables.

**Function Signature:**

1. `void swap_pointers(int* ptr1, int* ptr2);`

**Input:**

- `ptr1`: A pointer to an integer.
    
- `ptr2`: A pointer to an integer.
    

**Output:**

The function should modify the values stored at the memory locations pointed by `ptr1` and `ptr2`, effectively swapping their values.

**Example:**

1. int a {5};
2. int b {10};

4. int* ptrA = &a;
5. int* ptrB = &b;

7. swap_pointers(ptrA, ptrB);

9. // After the function call, the values should be swapped.
10. // a == 10, b == 5

**Note:**

- Assume that both input pointers are valid and point to valid memory locations.

## Code:

```cpp nums
/* You do NOT have to write a main() function. 
The main() function is written by me
behind the scenes to call your function and test your code.
*/

void swapPointers(int* ptr1, int* ptr2) {
    //-- Write your code below this line

    
    
    
    //-- Write your code above this line
}
```