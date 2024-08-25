# Function Definition

Name:

- The Name of the Function
- Same Rules as for Variables
- Should be Meaningful
- Usually a Verb or Verb Phrase

Parameter List:

- The Variables Passed into the Function
- Their Types Must be Specified

Return Type:

- The Type of the Data That is Returned from the Function
- If the Function is not Expected to Return Anything then the Keyword `void` can be used.

Body:

- The Statements that are Executed when the Function is Called
- In Curly Braces {}

# Example with no Parameters

![](Pictures/Function%20Parameters.png)
Here we have a simple function definition, notice the name of the function is `function_name`. After the function name we have open and closed parenthesis, in this case this function **expects no parameters** so there's nothing inside the parenthesis. This function **returns an integer**, we specify that by providing the type of return value before the function name. Finally we have the **body** of the function which consists of statements inside curly braces. You can see that this is same syntax as we've used in our main function. 

Of course we can have functions that return nothing, expect many parameters and so fourth. The syntax for all of them is very regular and exactly what you would expect. 

Let's see another one.
# Example with Parameters
![](Pictures/Function%20with%20Parameter.png)
In this case we have the same function named `function_name` but this time it expects exactly one **parameter**, that parameter is an integer type and it's available for us to use in the **body** of the function.
# Example with no Return Type (void)
![](Pictures/Function%20with%20no%20Return%20Type.png)
In this example we have a function that returns nothing when called. In this case we provide the keyword `void` before the function name, this tells the compiler that there is no **return type**. With `void` functions we can still have simple return statements in the body of the function, but they're totally optional and not often written. If there is no return statement, it's understood that the function returns after the last statement is executed. 

Pretty simple syntax, let's look at one more.

# Example with Multiple Parameters

![](Pictures/Example%20with%20Multiple%20Parameters.png)
In this example we see a function definition for `function_name` that expects multiple parameters. In this case the functions expects two parameters, an integer and a standard string. When the function is called these two parameters must be provided as arguments in the same order as specified in the parameter list.

# Example with no Return Type and no Parameters

Suppose we want to write a function that displays "Hello" followed by an end line every time it's called. We could easily define that function as follows: 
```cpp
void say_hello(){
	cout << "Hello" << endl;
}
```

The function name is `say_hello()`, it expects no parameters, and returns nothing. In the body of the function we have an output statement that just displays "Hello". Notice that in this case there is no return statement required since the function doesn't return anything.
# Calling Functions

Once the `say_hello()` function is defined we can call it from `main()` or from any other function.
```cpp
void say_hello(){
	cout << "Hello" << endl;
}

int main(){
	say_hello();
	return 0;
}
```

In this example you see the function `say_hello()` defined above and you also see that it's being called by the `main()` function below. This program will display "Hello". 

```cpp
void say_hello(){
	cout << "Hello" << endl;
}

int main(){
	for (int i{1}; i<=10; ++i)
		say_hello();
	return 0;
}
```

In this example we're calling the `say_hello()` function 10 times inside a `for` loop inside the `main()` function, this will display "Hello" 10 times, once per line.

```cpp
void say_world(){
	cout << " World" << endl;
}

void say_hello(){
	cout << "Hello" << endl;
	say_world();
}

int main(){
	say_hello();
	return 0;
}
```

Of course we can define as many functions as we need in our applications to help modularize our program. In this case we're defining 3 functions, `say_world()`, `say_hello()` and `main`. Execution always begins with the main function, so in this case `main` calls `say_hello()` so we execute `say_hello()` and we display "Hello" to the console. But then `say_hello()` calls `say_world()` and we display " World". So this program displays "Hello World" to the console. 

Here's the same example with some other output statements sprinkled in:
![](Pictures/Calling%20a%20Function.png)
Again, execution always begins with the main function. So in this case `main()` calls `say_hello()` so we execute `say_hello()`. Remember that when `say_hello()` is finished we need to complete the code in `main()`. So we display "Hello" to the console, then `say_hello()` calls `say_world()` and when `say_world()` is done we complete the code in `say_hello()`. So we execute `say_world()` and it displays " World" to the console followed by "Bye from say_world" and then we go back to where we left off in `say_hello()` and print "Bye from say_hello" to console. Then we go back to where we left off in `main()` and print "Bye from main" to console and our program terminates. 

You can walk through this code and see exactly what's happening.

Note: Compiler must know the function details **BEFORE** it is called!

```cpp
int main(){
	say_hello(); // called BEFORE it is defined ERROR
	return 0;
}

void say_hello(){
	cout << "Hello" << endl;
}
```

In this example `say_hello()` has been called in `main()` before it has been defined and so the compiler has not seen it yet. This will result in a compiler error informing you that `say_hello()` has not been declared in this scope. 

# Example Area of a Circle and Volume of a Cylinder

```cpp
// Section 11
// Function Definitions
// Area of a Circle and Volume of a Cylinder

#include <iostream>

using namespace std;

const double PI{3.141589};
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
    cout << "The volume of a cylinder with radius " << radius 
	    << " and height " 
        << height << " is " << calc_volume_cylinder(radius,height) 
	    << endl;
}

int main(){
    area_circle();
    volume_cylinder();
}
```
