# Function Parameters

- When we call a function we can pass in data to that function.

- In the function call they are called arguments.

- In the function definition they are called parameters.

- They must match in number, order, and in type.

## Example: Function with Return Statement

```cpp
int add_numbers (int, int);        // prototype

int main(){
	int result{0};
	result = add_numbers(100,200); // call
	return 0;
}

int add_numbers(int a, int b){     // definition
	return a + b;
}
```

In this example we have a function prototype that tells the compiler that we'll define a function named `add_numbers()` that expects two integers and returns an integer then in `main()` we declare an integer named `result` and initialize it to zero.  Then we call the `add_numbers()` function and pass in the integer literals 100 and 200, the compiler will type check this function call to be sure that it's valid. Since we're passing in two integers and the function prototype expects exactly that, the compiler will not produce an error. 

We can see at the bottom of the example that we've defined the `add_numbers` function, it has two integer parameters: a and b. In the case of the function call in `main()`, a will be 100 and be will be 200. 100 + 200 is computed and 300 is returned, 300 is then assigned to the variable `result` in the `main()` function.

Let's take a look at another example.
## Example: Void Function with String Argument.

```cpp
void say_hello(std::string name){
	cout << "Hello " << name << endl;
}

say_hello("Frank");

std::string my_dog{"Buster"};
say_hello(my_dog);
```

In this example the function prototype was not included to save space but it can be assumed moving forward that the prototype is always being declared, just not shown in the example code blocks. 

Notice that the function `say_hello()` expects one parameter and it's a C++ String Object. The function displays "Hello " and then whatever is inside the String Object. 

The next 3 statements would normally be in `main()` or inside another function, these are the function calls. The first is `say_hello("Frank")`, notice that "Frank" is a C Style String Literal, but the function expects a C++ String Object, aren't these types different? Why does the compiler not produce an error here? Yes, the types are different, but the compiler will try to convert one type to another if it knows how to make the function call work. In this case the C Style Literal String "Frank" is converted into a C++ String Object, the same would happen if a function expected a double but an integer was provided. The integer would be promoted into a double as we've already seen. 

Notice the last function call, in this case we are calling the function `say_hello()` with a single String Object parameter `my_dog` which is a variable name for a String Object with the string "Buster" inside of it.

Let's talk a bit about how parameters are passed into functions. 
# Pass-By-Value

- When you pass data into a function it is passed-by-value.
- A copy of the data is passed to the function.
- Whatever changes you make to the parameter in the function does **not** affect the argument that was passed in.

## Formal vs. Actual Parameters:

- Formal Parameters - the parameter defined in the function header.
- Actual Parameters - the parameter used in the function call, the arguments.

## Example: Actual vs. Formal Parameters

```cpp
void param_test(int formal){    // formal is a copy of actual
	cout << formal << endl;     // 50
	formal = 100;               // only changes the local copy
	cout << formal << endl;     // 100
}

int main(){
	int actual{50};
	cout << actual << endl;     // 50
	param_test(actual);         // pass in 50 to the param_test
	cout << actual << endl;     // 50 - did not change
	return 0
}
```

In this example we have a function definition for a function called `param_test()`, and this function expects one parameter called `formal`. This is an example of a "formal" parameter. If this function expected more than one parameter they would all be considered formal parameters.

In the `main()` function we're declaring an integer named `actual` and initializing it to 50. Then we're displaying `actual` which will display 50 and we're calling the `param_test` function with the actual parameter. This is the function call, any parameters passed to the function here are considered "actual" parameters. In this case, the value of the "actual" parameter is copied into "formal" parameter. So `formal` in the `param_test` function will have the value 50 but it's in a different location in memory than `actual` because it a copy was made. 

We then display `formal` in `param_test` so 50 is displayed, then we assign 100 to formal and display it again. Now the function is done and we return back to `main()` and we print `actual`, `actual` will still be 50, it was never changed because `param_test` was working with a copy all along. 

It's very important to understand the concept of pass by value since it's critical to understanding functions. Let's have a look at the function `return` statement next.
# Function Return Statement

- If a function returns a value then it must use a `return` statement that returns a value.
- If a function does not return a value(`void`) then the `return` statement is optional.
- `return` statement can occur anywhere in the body of the function.
- `return` statement immediately exits the function.
- We can have multiple `return` statements in a function although you want to avoid having many `return` statements in a function.
- The return value is the result of the function call.

 # Examples From the IDE

```cpp
// Section 11
// Function Parameters

#include <iostream>
#include <string>
#include <vector>

using namespace std;

void pass_by_value1(int num);
void pass_by_value2(string s);
void pass_by_value3(vector<string> v);
void print_vector(vector<string> v);

void pass_by_value1(int num){
    num = 1000;
}

void pass_by_value2(string s){
    s = "Changed";
}

void pass_by_value3(vector<string> v){
    v.clear(); // delete all vector elements
}

void print_vector(vector<string> v){
    for (auto s : v){
        cout << s << " ";
    cout << endl;
    }
}

int main(){
    int num{10};
    int another_num{20};

    cout << "num before calling pass_by_value1: " << num << endl;
    pass_by_value1(num);
    cout << "num after calling pass_by_value1: " << num << endl;

    cout << "\nanother_num before calling pass_by_value1: "
        << another_num << endl;
    pass_by_value1(another_num);
    cout << "another_num after calling pass_by_value1: " 
        << another_num << endl;

    string name{"Frank"};
    cout << "\nname before calling pass_by_value2: " 
        << name << endl;
    pass_by_value2(name);
    cout << "name after calling pass_by_value2: "
        << name << endl;

    vector<string> stooges{"Larry", "Moe", "Curly"};
    cout << "\nstooges bofore calling pass_by_value3: " << endl;
    print_vector(stooges);
    pass_by_value3(stooges);
    cout << "\nstooges after calling pass_by_value3: " << endl;
    print_vector(stooges);
}
```

## Output:

```
num before calling pass_by_value1: 10
num after calling pass_by_value1: 10

another_num before calling pass_by_value1: 20
another_num after calling pass_by_value1: 20

name before calling pass_by_value2: Frank
name after calling pass_by_value2: Frank

stooges bofore calling pass_by_value3: 
Larry 
Moe 
Curly 

stooges after calling pass_by_value3: 
Larry 
Moe 
Curly 
```

