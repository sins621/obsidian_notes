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

```cpp nums
#include <iostream>

using namespace std;

void double_data(int *fn_int_ptr) { *fn_int_ptr *= 2; }

int main() {
  int value{10};
  int *int_ptr{nullptr};

  cout << "Value " << value << endl;
  double_data(&value);
  cout << "Value " << value << endl;

  cout << "-----------------------------" << endl;
  int_ptr = &value;
  double_data(int_ptr);
  cout << "Value " << value << endl;

  cout << endl;
  return 0;
}
```

In this program all the function does is doubles whatever it's pointing to.

We'll call the function in two parts, first by passing in the memory location of the `value` variable:

```cpp
cout << "Value " << value << endl;
double_data(&value);
cout << "Value " << value << endl;
```

And second by assigning a pointer to the memory location of the `value` variable and passing that into the function:

```cpp
int_ptr = &value;
double_data(int_ptr);
cout << "Value " << value << endl;
```

Let's see how this looks on the stack:

## The Stack

### Initialization:

![](Pictures/Passing%20Pointers%20to%20Functions%20Initialization.png)

First we initialize two variables, `value` and `int_ptr` and we can imagine that their memory addresses are 1000 and 2000 respectively.

## `double_data` function

