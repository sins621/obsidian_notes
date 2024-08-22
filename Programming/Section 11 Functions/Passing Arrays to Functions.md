# Introduction

- We can pass an array to a function by providing square brackets in the formal parameter description.

	`void print_array(int numbers []);`

- The array elements are **NOT** copied.

- Since the array name evaluates to the location of the array in memory - this address is what is copied.

- So the function has no idea how many elements are in the array since all it knows is the location of the first element (the name of the array)

# Example: Print Array

```cpp
void print_array(int numbers[]);

int main (){
	int my_numbers[] {1,2,3,4,5};
	print_array(my_numbers);
	return 0;
}

void print_array(int numbers[]){
	// Doesn't know how many elements are in the array???
	// We need to pass in the size!!
}
```

In this example you can see that both the function prototype, and the function definition have square brackets after the formal parameter name. This tells the compiler that the function expects an array of integers in this case, so far so good, then in main we have an array of 5 integers called `my_numbers[]` and it's been initialized to the integers 1 through 5. 

So we call the `print_array()` function and pass in the array `my_numbers[]`, all good so far, now we execute the `print_array()` function but we have no idea how many times to iterate since the array name has no size information we're stuck. If the array has a sentinel value, like a C-Style String does, we can iterate until we see the sentinel value but in this case the `my_numbers[]` array has no such sentinel value. There's no way we can write this function body in a way where it will work with any array of integers.

So the solution is to pass in the size of the array to the function as well, let's do that next.

# Example: Size Passed Through

```cpp
void print_array(int numbers[], size_t size);

int main (){
	int my_numbers[] {1,2,3,4,5};
	print_array(my_numbers, 5);
	return 0;
}

void print_array(int numbers[]){
	for (size_t{0}; i < size; ++i)
		cout << numbers[i] << endl;
}
```

Now we've added a size parameter to both the function prototype and the function definition. In `main()` when we call the function we pass in `my_numbers` and the size of the array which is 5 in this case. 

Now when we execute the body of the `print_array()` function we know the location of the array which is the array name and we know how many elements are in the array. We can write a `for` loop now that iterates through the array and displays every integer. 

This looks great but there is one potential gotcha that you need to be aware of.
# Example: Unintentionally Modifying the Contents of the Array

Since we are passing the location of the array:

	 The Function can modify the actual array!

Since we're passing in to the function the location of the actual array that was declared in `main()`, that means that we can modify the actual array inside the function. This could be useful in the case of a function like `zero_array()` that we can call whenever we want to zero out all the elements in an array, however in the `print_array()` function we don't want to modify the array, if we do it's probably an unintentional error. 

We'll see how to protect ourselves from this kind of error in the next example, but first let's see how we can write a useful function like `zero_array()`.

```cpp
void zero_array(int numbers[], size_t size){
	for (size_t i{0}; i < size; ++i)
		numbers[i] = 0;       // zero out array element
}

int main(){
	int my_numbers[]{1,2,3,4,5};
	zero_array(my_numbers, 5);     // my_numbers is now zeroes!
	print_array(my_numbers, 5);    // 00000
}
```

In this case the `zero_array()` function receives the location of the array and the size of the array. We can simply iterate through the array and set each array element to zero, notice that when we print the array in `main()` after we call `zero_array()` all the array elements are now zero. 

So let's get back to seeing what we can do to have the compiler help us so we don't change the an array when we don't want to.
# Const Parameters

We can tell the compiler that the function parameters are const(read-only).

This could be useful in the `print_array()` function since it should **NOT** modify the array.

```cpp
void print_array(const int numbers[], size_t size){
	for (size_t i{0}; i < size; ++i)
		cout << numbers[i] << endl;
	numbers[i] = 0; /* any attempt to modify 
	the array will result in a compiler error*/
}
```

In this case notice that we included the `const` keyword right before the array parameter declaration, that's it, now if we try to modify any array element as we do in the assignment statement a compiler error will occur. Depending on your compiler the error message will say something along the lines of "Error, trying to assign to a read-only value".

The idea of passing the location of a variable to a function instead of the valuable of the variable is fundamental in understanding the next topic we'll talk about, it's called pass by reference. 
# Coding Exercise: Passing Arrays to Functions - Print a Guest List

In this exercise you will create a program that will be used to `print` the `guest_list` to an event and then `clear` the `guest_list` when the event is over.

Begin by completing the function prototypes `print_guest_list` and `clear_guest_list` which are both `passed an array of std::string and a size_t value`. Ensure that the array cannot be modified within the `print_guest_list` function by using the keyword `const` in the parameter list.

Now that the function prototypes have been declared, at the bottom of the file define both functions.

Both the `print_guest_list` and `clear_guest_list` functions will be passed the `array argument` `guest_list` and the `size_t argument` `guest_list_size` which have both been provided to you.

The `print_guest_list` function should print the values contained within the `guest_list` from left to right with each element being printed on a new line.  Use a `for loop` to iterate through the array.

The `clear_guest_list` function should replace each element of the array with the string value `" "`, a single space.  Use a `for loop` to iterate through the array.

Now, from the function body of `event_guest_list`, make the following function calls in this order:

`print_guest_list`

`clear_guest_list`

`print_guest_list`

and passing the `array argument` `guest_list` and the `size_t argument` `guest_list_size` with each function call.

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <iostream>
#include <string>
#include <typeinfo>
using namespace std;

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE THE FUNCTION PROTOTYPES BELOW THIS LINE----

string print_guest_list(            );//----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES
void clear_guest_list(            );//----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES
                                      
//----WRITE THE FUNCTION PROTOTYPES ABOVE THIS LINE----                                      
//----DO NOT MODIFY THE CODE BELOW THIS LINE----

void event_guest_list() {

    string guest_list[] {"Larry", "Moe", "Curly"};
    size_t guest_list_size {3};

    //----DO NOT MODIFY THE CODE ABOVE THIS LINE----
    //----WRITE THE FUNCTION CALLS BELOW THIS LINE----

    
    
    

    //----WRITE THE FUNCTION CALLS ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
}

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE THE FUNCTION DEFINITION BELOW THIS LINE----

string print_guest_list(            ) {//----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES

    //----WRITE THE FUNCTION BODY BELOW THIS LINE----
    
    
    
        
    //----WRITE THE FUNCTION BODY ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    return typeid(guest_list).name();
}

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE THE FUNCTION DEFINITION BELOW THIS LINE----

void clear_guest_list(            ) {//----WRITE THE FUNCTION PARAMETER LIST WITHIN THEPARENTHESES

    //----WRITE THE FUNCTION BODY BELOW THIS LINE----
    
    
    
    
    //----WRITE THE FUNCTION BODY ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
}
```