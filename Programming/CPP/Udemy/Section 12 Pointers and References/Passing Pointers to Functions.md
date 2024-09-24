# Introduction

- Pass-by-Reference with Pointer Parameters.

- We can use Pointers and the Dereference Operator to Achieve Pass-by-Reference.

- The Function Parameter is a Pointer.

- The Actual Parameter can be a Pointer or Address of a Variable.

# Pass-by-Reference with Pointers - Defining the Function

In this example we're declaring a function prototype and then defining the function. The function is called double data and it expects a pointer to an integer as a parameter, notice it doesn't return anything.

Instead we'll double the contents of the data it points to.

```cpp nums
void double_data(int *int_ptr);

void double_data(int *int_ptr){
	*int_ptr *= 2;

	// *int_ptr = *int_pt * 2;
}
```

So in the body of the function we simply dereference the pointer and multiply what it points to by 2 and assign it back, remember the asterisk is used to dereference a pointer. 
# Pass-by-Reference with Pointers - Calling the Function

Since the function parameter above is a **pointer to an integer** that means it's expecting a **memory address** of an integer. 

```cpp nums
int main(){
	int value{10];
	cout << value << endl;          // 10
	double_data(&value);
	cout << value << endl;          // 20       
}
```

In this case we have an integer named `value` with 10 assigned to it, we can call `double_data` and pass in the location of the variable using the ampersand symbol which is the 'address of' operator.

When we return from the function we now display value which is doubled to 20. 
# Examples in the IDE:
