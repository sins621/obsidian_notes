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

## Example 1:

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
### The Stack

#### Initialization:

![](Pictures/Passing%20Pointers%20to%20Functions%20Initialization.png)

First we initialize two variables, `value` and `int_ptr` and we can imagine that their memory addresses are 1000 and 2000 respectively.

### `double_data` function

#### Pass in Address

![](Pictures/Passing%20Pointers%20to%20Functions%20-%20double_data%20function.png)

Now we pass in the address of `value` to the function, then we dereference the pointer, `fn_int_ptr`, inside the function and multiply the value it points to by two. 

![](Pictures/Passing%20Pointers%20to%20Functions%20-%20pop%20double_data%20off.png)

Now we pop the `double_data` function off the stack and return to `main`. We can see that `value` is now equal to 20 as it has been modified through the function. When we now output the value the output will be 20.

#### Pass in Pointer

![](Pictures/Passing%20Pointers%20to%20Functions%20-%20Passing%20Pointer.png)

In this example we assign `int_ptr` to the memory address of `value` which in our example is 1000. We then pass the pointer into the function and essentially do the same thing again because when we dereference the pointer in the function we will be manipulating the contents of `value`. We multiply by 2 which in this case will modify `value` to be 40 and we output that value.

## Example 2:

```cpp nums
#include <iostream>
#include <string>
#include <vector>

using namespace std;

void swap (int *a, int *b){
  int temp = *a;
  *a = *b;
  *b = temp;
}

int main(){
  int x{100}, y{200};
  cout << "\nx: " << x << endl;
  cout << "y: " << y << endl;

  swap(&x, &y);

  cout << "\nx: " << x << endl;
  cout << "y: " << y << endl;

  cout << endl;
  return 0;
}
```

### The Stack:

![](Pictures/Passing%20Pointers%20to%20Functions%20-%20The%20stack.png)

The purpose of this program is to swap two integers, we declare two of them and initialize them to 100 and 200 respectively. 

After declaration we're going to output `x` and `y`, you can guess what that output will contain.

### The `swap` Function

![](Pictures/Passing%20Pointers%20to%20Functions%20-%20Swap%20Function.png)

Once we reach this function we pass the memory locations of `x` and `y` into our `swap` function. Just as before in this example we assume the memory locations are 1000 and 2000 respectively and so we can assume that pointer `a` and pointer `b` now contain those values. 

We create an integer variable called `temp` and assign it to `a` dereferenced, meaning it is assigned the value that `a` points to which in this case is `x` which in this case holds 100 and so 100 is assigned to `temp`.

![](Pictures/Passing%20Pointers%20to%20Functions%20-%20Swap%20Function%20Completion.png)

Moving through the function we assign `a`, dereferenced, to `b`, dereferenced, meaning that `x` is assigned the value of `y` which is 200. We then assign `b`, dereferenced, to the value of `temp` which in this case is 100 resulting in the `y` value being changed to 100 effectively swapping these values.

### Back to Main:

![](Pictures/Passing%20Pointers%20to%20Functions%20-%20Back%20To%20Main.png)

Now we return to main, the values have been swapped and the output is as follows:

```
x: 100
y: 200

x: 200
y: 100
```

## Example 3:

```cpp nums
#include <iostream>
#include <string>
#include <vector>

using namespace std;

void display(vector<string> *v) {
  for (auto str : *v)
    cout << str << " ";
  cout << endl;
}

void display(int *array, int sentinel);

int main() {

  cout << "-------------------------------------" << endl;
  vector<string> stooges{"Larry", "Moe", "Curly"};
  display(&stooges);
}
```

