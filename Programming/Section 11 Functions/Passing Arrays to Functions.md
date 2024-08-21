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