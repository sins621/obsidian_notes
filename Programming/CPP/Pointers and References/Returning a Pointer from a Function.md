# Introduction

- Functions Can Also Return Pointers

	`type *function();`

- Should Return Pointers to:

	- Memory Dynamically Allocated In The Function
	- To Data That Was Passed In

- Never Return A Pointer To A Local Function Variable!
# Returning a Pointer

```cpp nums
int *largest_int (int *int_ptr1, int *int_ptr2){
	if (*int_ptr > *int_ptr2)
		return int_ptr1;
	else
		return int_ptr2;
}
```

In this example we're creating a function that returns an integer pointer variable. We pass two variables in as arguments and then compare the values they point to to one another. 

Notice that we are dereferencing the pointers in the if statements, comparing their values and then returning a pointer variable, not the information it points to.
# Returning a Parameter

```cpp nums
int main(){
	int a {100};
	int b {200};
	
	int *largest_ptr {nullptr}
	largest_ptr = largest_int(&a, &b)
	cout << *largest_ptr << endl;        // 200
}
```

In this example we declare two integers, `a` and `b`. We create a pointer to an integer called `*largest_ptr` and we assign `nullptr` to it, then we assign a new value to it by calling the `largest_int` function which expects the memory location of two integers and so we dereference `a` and `b` and pass those in. 

The function will return the memory address that points to the largest integer and assign that memory location to our `largest_ptr` variable, finally we dereference the pointer and output the value it points to which is 200.
# Returning Dynamically Allocated Memory
## Function Definition

In this example we are creating a function that is designed to allocate space for a new array on the heap dynamically while the program was running which is something we couldn't do previously

```cpp nums
int *create_array(size_t size, int init_value = 0){
	int *new_storage {nullptr};

	new_storage = new int [size];
	for (size_t i{0}; i < size; ++i)
		*(new_storage + i) = init_value;
	return new_storage;
}
```

First we create a function named `*create_array` which returns an integer pointer and expects a `size_t` variable named `size` and an integer variable named `init_value`. The `size_t` variable is used to determine the size of the array and the integer is used to determine the default value assigned to each new array element which in this case is 0.

**Note:** If you remember, you can assign default values as array arguments which in this case is 0, so if the function is called and only the first of the two arguments is specified, ie. the size, then every element in the array will have it's assigned value defaulted to 0.

Now we create a new pointer to an integer named `*new_storage` and assign `nullptr` to it, allocate memory on the heap with the `new` keyword using the `size` variable we passed in as an argument to specify the size of our array.

Then we use a for loop to iterate through all array elements assigning the value of the `init_value` variable to each element. Notice that we use the `size` variable to increment the memory location that our pointer is pointing to.

**Note:** While we are using a `size_t` variable to increment a pointer to an integer, this is not a problem as the pointer is incremented based on the size of the type it points to, not the size of the index variable `i` used in this case.

Finally we return the pointer which now points to an array of integers.
## Calling the Function

```cpp nums
int main() {
	int *my_array;      // will be allocated by the function

	my_array = create_array(100,20); // create the array
	// use it
	delete [] my_array; // be sure to free the storage
}
```

In this example we create a new pointer to an integer named `*my_array` and we use the new function that we have created to allocate an array to this pointer by calling it on line 4.

We pass in 100 as the size and 20 as the default value, now `*my_array` points to an array with 100 elements which all have default values of 20, we can then use the array but we **must** be sure to delete the array, or in other words free up that storage in memory, when we are done using it.
# Never Return A Pointer To A Local Variable!

```cpp nums
int *dont_do_this(){
	int size {};
	...
	return &size;
}
int *or_this(){
	int size{};
	int *int_ptr {&size};
	...
	return int_ptr;
}
```

# In the IDE:
## Main:

![](Pictures/Returning%20a%20Pointer%20from%20a%20Function%20Main%20till%20Call.png)


First we create a pointer to an `integer`, call it `*my_array` and initialize it to `nullptr`. We then create a `size_t` variable named `size` and an `integer` named `init_value`. In our example let's imagine `size_t` is equal to 10 and `init_value` is equal to 2. 

Now we assign a value to `my_array` by calling the `create_array` function and passing in our size and initial value variables.
## Create Array Function:

![](Pictures/Returning%20a%20Pointer%20from%20a%20Function%20Create%20Array%20Function.png)

When we call the `create_array` function the first thing we're going to do is create a new int pointer named `new_storage` and initialize it to `nullptr`. We then allocate size on the heap for an array at that memory location by using the `new` keyword and and passing in our `size` variable that was provided as an argument to the function.

**Note:** `size` is passed by value so in this function it is a *copy* of the variable in main.

The `size` variable dictates how large our array is, we then use a `for` loop as we have in previous examples to assign all values of the array to 2 and finally we return the memory location of this newly created array.
## Back to Main:

![](Pictures/Returning%20a%20Pointer%20from%20a%20Function%20Back%20to%20Main.png)

Now the `create_array()` function is popped off the stack and the `my_array` pointer has had the memory location of our newly created array assigned to it.
## Display Function:

![](Pictures/Returning%20a%20Pointer%20from%20a%20Function%20Display%20Function.png)

Now we've called the `display()` function. The purpose of this function is to display each element of the array separated by a space. We pass the memory location of our array to it as a constant integer pointer to a constant array, this way we guarantee that we won't accidentally modify the contents of the array when we don't intend to.

**Note:** In this instance we iterating over each element of the array using the *subscript* *operator* instead of performing pointer arithmetic as we did in the last example.
## Back to Main: (Again)

![](Pictures/Returning%20a%20Pointer%20from%20a%20Function%20Delete%20Array.png)

Finally we return to `main()` once again but we make sure to delete the array off the heap so that we can free that memory up for other programs to use.