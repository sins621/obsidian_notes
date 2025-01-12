# Introduction:

- We can have functions that have different parameter lists that have the same name.

- Abstraction mechanism since we can just think 'print' for example.

- A type of polymorphism.

	- We can have the same name work with different data types to execute similar behavior.

- The compiler must be able to tell the functions apart based on the parameter lists and arguments supplied.

# Example: `ints` and `doubles`

```cpp
int add_numbers(int,int);            // add ints
double add_numbers(double, double);  // add doubles

int main(){
	cout << add_numbers(10,20) << endl;      // integer
	cout << add_numbers(10.0,20.0) << endl;  // double
}
```

In this example we have two functions that are both called `add_numbers()` The first function expects two integers and the second function expects two doubles. We're only showing the function prototypes in this slide but we actually have to implement both functions, we'll do that in the next slide. 

Notice that in `main()` we're calling both functions, but we don't have to think about different names. We just want to add two numbers. If we call the `add_numbers` function with two doubles then the `double, double` version is called and if we call the version with two integers then the `int, int` version is called. 

# Example: `ints` and `doubles` Function Definition

```cpp
int add_numbers(int a, int b){
	return a+b;
}

double add_numbers (double a, double b){
	return a+b;
}
```

In this example we're providing the function definitions for the `add_numbers` functions that we prototyped in the previous example. It's important to understand that we must implement all of the overloaded versions.

Notice that the code for these two functions is nearly identical except for the types, C++ has a feature called function templates that allow us to just write one generic version of the `add_numbers` function and it will take care of providing the correct version when called. Function templates are a little bit more of an advanced topic, and we'll discuss it when we talk about the standard template library.

Let's take a look at another example:

# Example: Many Prototypes of Different Types

```cpp
void display(int n);
void display(double d);
void display(std::string s);
void display(std::string s, std::string t);
void display(std::vector<int> v);
void display(std::vector<std::string> v);
```

In this example we're only looking at the function prototypes but remember, we'd have to implement all of these. We have five functions named display, the parameter list for these functions must be different so the compiler can tell them apart. Once these functions are implemented, we can call `display()` and pass in our data, the compiler will check the argument type in the function and match it to one of the available overloaded display functions. If it can't match it, or if it can't convert the argument to one that matches, then we'll be presented with a compiler error. 

# Example: Return Type is not Considered

```cpp
int get_value();
double get_value();

// Error

cout << get_value() << endl; // which one?
```

There is one restriction to function overloading, the return type is not considered when the compiler is trying to determine which function to call. Here we have two overloaded functions, both called `get_value()` and both expect no parameters, the only difference is that one returns an integer and the other a double. This will produce a compiler error since the only difference is the return type.

Consider the output statement at the bottom of the code block, which function would the compiler call? It could call either, and that's the problem, it won't guess, so it will produce a compiler error. Overloading functions is used extensively in object orientated design and we'll see it again when we design our own C++ Object Orientated Classes. 

# Example: Multiple Print Functions

```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

void print(int);
void print(double);
void print(string);
void print(string,string);
void print(vector<string>);

void print(int num){
    cout << "Printing int: " << num << endl;
}
void print(double num){
    cout << "Print double: " << num << endl;
}
void print(string s){
    cout << "Printing string: " << s << endl;
}
void print(string s, string t){
    cout << "Printing 2 strings: " << s << " and " << t << endl;
}
void print(vector<string> v){
    cout << "Printing vector of strings: ";
    for (auto s: v)
        cout << s + " ";
    cout << endl;
}

int main(){
    print(100); // int
    print('A'); // character is always promoted to int should print 65 ASCII ('A)
    print(123.5); // double
    print(123.5F); // Float is promoted to double
    print("C-style string"); // C-style string is converted to a C++ string
    string s{"C++ string"};
    print(s); // C++ string
    print("C-style string", s); // First argument is converted to a C++ string 
    vector<string> three_stooges{"Larry", "Moe", "Curly"};
    print(three_stooges);
}
```

# Section Exercise

In this exercise you will create a program that computes the area of two shapes, a `square` and a `rectangle`, by calling the overloaded function `find_area`.

Begin by declaring the function prototypes for the `square` `find_area` function and the `rectangle` `find_area` function.

The `square` `find_area` function is `passed an integer value` and `returns an integer value`.

The `rectangle` `find_area` function is `passed two double values` and `returns a double value`.

Remember that both function prototypes should have the same function name `find_area`.

Now that the function prototypes have been declared,  at the bottom of the file define both functions.

The `square` `find_area` function will be passed the argument `side_length` and return the area of the `square`. The formula for the area of a `square` is `side_length*side_length` . You may use the `<cmath>` function `pow` to compute this value if you wish.

The `rectangle` `find_area` function will be passed the arguments `length` and `width` and return the area of the `rectangle`. The formula for the area of a `rectangle` is `length*width`.

Now, from the function body of `area_calc`, declare and initialize the variables `square_area` and `rectangle_area` by calling the `find_area` function and passing the appropriate arguments which are listed below.

The `square` has a `side_length` of `2`.

The `rectangle` has a `length` of `4.5` and a `width` of `2.3`.

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <iostream>
#include <cmath>
using namespace std;

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE YOUR FUNCTION PROTOTYPES BELOW THIS LINE----




//----WRITE YOUR FUNCTION PROTOTYPES ABOVE THIS LINE----
//----DO NOT MODIFY THE CODE BELOW THIS LINE----

void area_calc() {
    
    //----DO NOT MODIFY THE CODE ABOVE THIS LINE----
    //----WRITE YOUR FUNCTION CALLS BELOW THIS LINE----
    
    
    
    
    //----WRITE YOUR FUNCTION CALLS ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    
    cout << "The area of the square is " << square_area << "\n" << "The area of the rectangle is " << rectangle_area;
}

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE YOUR FUNCTION DEFINITIONS BELOW THIS LINE----


```


## My Solution:

```cpp
#include <iostream>
#include <cmath>
using namespace std;

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE YOUR FUNCTION PROTOTYPES BELOW THIS LINE----

int find_area(int);
double find_area(double,double);

//----WRITE YOUR FUNCTION PROTOTYPES ABOVE THIS LINE----
//----DO NOT MODIFY THE CODE BELOW THIS LINE----

void area_calc() {
    
    //----DO NOT MODIFY THE CODE ABOVE THIS LINE----
    //----WRITE YOUR FUNCTION CALLS BELOW THIS LINE----
    
    int square_area{find_area(2)};
    double rectangle_area{find_area(4.5,2.3)};

    //----WRITE YOUR FUNCTION CALLS ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    
    cout << "The area of the square is " << square_area << "\n" << "The area of the rectangle is " << rectangle_area;
}

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE YOUR FUNCTION DEFINITIONS BELOW THIS LINE----

int find_area(int side_length){
    return pow(side_length,2);
}

double find_area(double side_length, double side_width){
    return side_length * side_width;
}

int main(){
    area_calc();
}
```

