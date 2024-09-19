# Introduction

The compiler must 'know' about a function before it is used.

## Define functions before calling them:

- OK for small programs.
- Not a practical solution for larger programs.

## Use function prototypes

- Tells the compiler what it needs to know without a full function definition.
- Also called forward declarations.
- Placed at the beginning of a program.
- Also used in our own header files (.h) - more about this later.

# Example: Simple Function

```cpp
int function_name(); // prototype

int function_name(){
	statements(s);
	return 0
}
```

The function prototype for this function is the first line of code you see. Notice that it looks very much like the function header, that's the part of the function definition right before the body of the function. With the function prototype the compiler doesn't need to know what the implementation of the function is, only it's header information. 

So in this case it knows that we'll later define a function named `function_name()` that expects no parameters and expects an integer. If we use a function named `function_name()` it'll enforce those conditions, if we try to use it in any other way, say by calling it with an integer in the parameter list, we'll be presented with a compiler error. 

You can have as many prototypes as you need, one per function, and it doesn't matter what order you declare them in. Let's take a look at another.

# Example: With Parameters

```cpp
int function_name(int);     // prototype
                            // or
int function_name(int a);   // prototype

int function_name(int a){
	statements(s);
	return 0;
}
```

In this case we have the same function named `function_name` but this time it expects exactly one parameter, so we provide a function prototype to the compiler that has an `int` in the parameter list. Note that we can supply the name of the parameter if we wish but it isn't used by the compiler. The compiler doesn't care about the name, only the type so either of these function prototypes can be used. Best practice is to provide the parameter names for documentation purposes. 

Let's see another example.

# Example: Function With No Return

```cpp
voif function_name();    // prototype

void function_name(){
	statements(s);
	return; // optional
}
```

In this example we have a function that returns nothing when called. So the function prototype must include the `void` keyword prior to the function name, just like the function definition does.

# Example: Function Function With Two Parameters

```cpp
void function_name(int a, std::string b);
// or 
void function_name(int, std::string);

void function_name(int a, std::string b){
	statements(s);
	return; // optional
}
```

In this case the function expects two parameters, an `integer` and a `standard string`, so either one of the function prototypes above are valid. In one case we provide the parameter types and names, and in the other only the parameter types. 

# Example: A Function With No Return Type and No Parameters

```cpp
void say_hello();

void say_hello(){
	cout << "Hello" << endl;
}
```

The function prototype for the `say_hello()` function we saw in the previous lesson would look like this. 

## Calling a Function

So let's see how the compiler uses this information in the function prototype to help us write code:
```cpp
void say_hello();

int main(){
	say_hello();              // OK
	say_hello(100);           // Error
	cout << say_hello();      // Error
	                          // No return value
	return 0;
}
```

The function prototype here says that I'll define a function named `say_hello()` that expects no parameters and returns nothing, then I use/call the function in `main()`. 

The first function call is fine since it matches the prototype, the second function call will cause a compiler error. We told the compiler that the function expects no parameters but we're passing in an integer to the function call, the compiler won't allows this. 

The third function call is within an output statement, think about this one for a second, we're telling the compiler to display a value that `say_hello()` evaluates to but the function prototype says that the function `say_hello()`  doesn't return anything so the compiler presents us with an error.

# Example: Two Functions

```cpp
void say_hello(); // prototype
void say_hello(); // prototype

int main() {
	say_hello();
	cout << " Bye from main" << endl;
	return 0;
}

void say_world(){
	cout << " World" << endl;
	cout << " Bye from say_world" << endl;
}

void say_hello(){
	cout << "Hello" << endl;
	say_world();
	cout << Bye from say_hello" << endl;
}
```

Here is the same code that we saw in the previous lesson, however in this example we're providing function prototypes for the `say_hello()` and `say_world()` functions at the top of the file. Now the compiler knows about these functions and we can call them in any order we wish in our program and the compiler will make sure they're called as expected. 

# Example: Area of a Circle and Volume of a Cylinder

```cpp
// Section 11
// Function Prototypes
// Area of a Circle and Volume of a Cylinder

#include <iostream>

using namespace std;

// Function Prototypes
double calc_area_circle(double radius);
double calc_volume_cylinder(double radius, double height);
void area_circle();
void volume_cylinder();

const double PI{3.141589};

int main(){
    area_circle();
    volume_cylinder();
}

double calc_area_circle(double radius){
    return PI * radius * radius;
}

double calc_volume_cylinder(double radius, double height){
    //return PI * radius * radius * height;
    return calc_area_circle(radius) * height;
}

void area_circle(){
    double radius{};
    cout << "Enter the radius of the circle: ";
    cin >> radius;

    cout << "The area of a circle with radius " << radius 
        << " is: " << calc_area_circle(radius) << endl;
}

void volume_cylinder(){
    double radius{};
    double height{};
    cout << "Enter the radius of the cylinder: ";
    cin >> radius;
    cout << "\nEnter the height of the cylinder: ";
    cin >> height;
    cout << "The volume of a cylinder with radius " 
	    << radius << " and height " 
        << height << " is " 
        << calc_volume_cylinder(radius,height) << endl;
}
```