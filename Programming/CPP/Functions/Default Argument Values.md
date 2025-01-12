# Introduction

- When a function is called, all arguments must be supplied.
- Sometimes some of the arguments have the same values most of the time.
- We can tell the compiler to use default values if the arguments are not supplied.
- Default Values can be in prototype or definition, not in both.
	- Best Practice - In the prototype
	- Must Appear at the tail end of the parameter list.
- Can have multiple default values.
	- Must appear consecutively at the tail end of the parameter list.

# Example - no default arguments

```cpp
double calc_cost(double base_cost, double tax_rate);

double calc_cost(double base_cost, double tax_rate){
	return base_cost += (base_cost * tax_rate);
}

int main(){
	double cost{0};
	cost = calc_cost(100.0, 0.06);
	return 0;
}
```

In this example we have a function with no default arguments, in the next example we'll modify it so it does have a default argument. The function is called `calc_cost()` and it expects the base cost of an item and the tax rate. The function calculates the tax amount and adds that to the base cost and returns that value to the caller. In the main function we're calling the function with 100.0 as the base cost and 6% as the tax rate. In this case 106 is returned from the function and assigned to cost. 

That's pretty easy but if 98% of our customers will have a 6% tax rate we're forced to provide this value every time we call the function, why not let the compiler default the tax rate to 6% unless we tell it otherwise.

Let's do that in the next example.

# Example - single default argument

```cpp
double calc_cost(double base_cost, double tax_rate = 0.06);

double calc_cost(double base_cost, double tax_rate){
	return base_cost += (base_cost * tax_rate);
}

int main(){
	double cost{0};
	cost = calc_cost(200.0);
	cost = calc_cost(100.0, 0.08);
	return 0;
}
```

Here we have the same function except that the function prototype has been modified to provide a default value for the tax rate. Notice that the parameter `tax_rate` in the function prototype now has a default initialization to 0.06 added to it, this effectively tells the compiler that if this argument is not provided by the function call then use the value 0.06 for `tax_rate`. 

Now notice the two calls in the main function, the first call simply calls `calc_cost` with 200.0 as the which is the base cost. Since the argument for `tax_rate` is not provided the compiler will use 6% for the tax rate. 

In the second call we are providing the tax rate, in this case the compiler will use that and ignore the default value. 

This can be pretty handy, suppose we have a function that prints documents and we have to supply the document name, the printer to print to, the paper size, the resolution and so fourth. Again, most of the time we print to the default printer to the default settings but sometimes we need higher resolution or to use a different printer, you get the idea. In this case, we can provide multiple default parameters for everything except the document name which is always required, this makes writing the code much simpler.

Let's add another default value to the `calc_cost` function.
# Example - multiple default arguments

```cpp
double calc_cost(double base_cost, 
				 double tax_rate = 0.06, 
				 double shipping = 3.50,
				 );

double calc_cost(double base_cost, double tax_rate){
	return base_cost += (base_cost * tax_rate);
}

int main(){
	double cost{0};
	calc_cost (100, 0.08, 4.25);      // will use no defaults
	cost = calc_cost(100.0, 0.08);    // will use default shipping
	cost = calc_cost(200.0);    // will use default tax and shipping
	return 0;
}
```

In this example we'll calculate the cost of the item based off the base cost of the item, the sales tax and a shipping charge. As before, most of the times the sale tax will be 6%, and in this example the standard typical shipping charge is $3.50. Most customers will have a 6% tax rate and a $3.50 shipping charge. 

We can easily add a second default argument to this function, notice that in the function prototype we add another parameter named `shipping` and we default this value to $3.50. The function body now calculates the tax for the item, adds the shipping charge, adds this to the original cost of the item and returns the result to the caller. 

In the main function we're calling `calc_cost` in 3 different ways:
- In the first call we're providing all 3 arguments to the function, in this case no default values will be used and the tax rate will be 8%, and shipping will be 4.25$.
- In the second call we're providing the cost of the item and the tax rate of 8%, in this case the default value for shipping will be used but the tax rate will use the 8% we provided. 
- In the final example we're only providing the cost of the item, so in this case both default values will be used. The tax rate default to 6% and the shipping charge will default to $3.50.

Default argument values give us the ability to make our code less verbose and potentially prevent errors by using default values rather than having to supply all of the arguments to the function all the time.

In the next lesson we'll learn about function overloading.
# Example In the IDE

```cpp
#include <iostream>
#include <iomanip>
#include <string>

using namespace std;

// Function prototype with default arguments
double calc_cost(double base_cost, double tax_rate = 0.06, double shipping = 3.50);
void greeting(string name, string prefix = "Mr.", string suffix = "");

// Function definition without default arguments
double calc_cost(double base_cost, double tax_rate, double shipping) {
    return base_cost += (base_cost * tax_rate) + shipping;
}
void greeting(string name, string prefix, string suffix){
    cout << "Hello " << prefix + " " + name + " " + suffix << endl;
}

int main() {
    double cost{0};
    cost = calc_cost(100.0, 0.08, 4.25);  // Uses no defaults: 100 + 100*0.08 + 4.25

    cout << fixed << setprecision(2);
    cout << "Cost is: " << cost << endl; // 112.25

    cost = calc_cost(100.0, 0.08);       // Uses default shipping: 100 + 100*0.08 + 3.50
    cout << "Cost is: " << cost << endl; // 111.50

    cost = calc_cost(200.0);             // Uses default tax rate and shipping: 200 + 200*0.06 + 3.50
    cout << "Cost is: " << cost << endl; // 215.50

    greeting("Glenn Jones", "Dr.", "M.D.");
    greeting("James Rogers", "Professor", "Ph.D");
    greeting("Frank Miller", "Dr.");
    greeting("William Smith");
    greeting("Mary Howard", "Mrs", "Ph.D");
    cout << endl;
}
```

## Output:

```
Cost is: 112.25
Cost is: 111.50
Cost is: 215.50
Hello Dr. Glenn Jones M.D.
Hello Professor James Rogers Ph.D
Hello Dr. Frank Miller 
Hello Mr. William Smith 
Hello Mrs Mary Howard Ph.D
```

# Challenge:

Using Default Argument Values - Grocery List

In this exercise you will create a program that will be used to automatically print a grocery list. Most weeks the grocery list is the same and so you may begin by declaring the function prototype `print_grocery_list` which has the default argument values:

`mangos` = `13`

`apples` = `3`

`oranges` = `7`

The function `print_grocery_list` has no return statement and so the return type of the function prototype should be `void`.

**IMPORTANT:** Before declaring the function prototype, read the entire exercise to determine the proper order of arguments in the function parameter list. Remember that default argument values that do not change should be placed at the tail end of the parameter list, and those which change most often should be placed at the beginning.

Once the function prototype is declared, complete the parameter list of the function definition at the bottom of the file.

Now, print this weeks grocery list by calling the function `print_grocery_list` from the function body of `modify_grocery_list`.

The next week, you decide that you would like `5 apples` instead of `3`. Print the new grocery list by calling the function `print_grocery_list` from the function body of `modify_grocery_list` and passing the new `apples` argument.

For the final week,  you are having a party and would like to serve a fruit punch so you will need `7 apples`, `11 oranges`, and the default number of `mangos`. Print the new grocery list by calling the function `print_grocery_list` from the function body of `modify_grocery_list` and passing the new `apples` and `oranges` arguments. 

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <iostream>
using namespace std;

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE YOUR FUNCTION PROTOTYPE BELOW THIS LINE----

void print_grocery_list()

//----WRITE YOUR FUNCTION PROTOTYPE ABOVE THIS LINE----
//----DO NOT MODIFY THE CODE BELOW THIS LINE----

void modify_grocery_list() {
    
    //----DO NOT MODIFY THE CODE ABOVE THIS LINE----
    //----WRITE YOUR FUNCTION CALLS BELOW THIS LINE----
    



    
    //----WRITE YOUR FUNCTION CALLS ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
}

void print_grocery_list(         ) { //----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES
                                     //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    cout << apples << " apples" << "\n" 
	    << oranges << " oranges" << "\n" 
	    << mangos << " mangos" << "\n";
}
```

## My Solution:

```cpp
#include <iostream>
using namespace std;

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE YOUR FUNCTION PROTOTYPE BELOW THIS LINE----

void print_grocery_list(int apples = 3, int oranges = 7, int mangos = 13);

//----WRITE YOUR FUNCTION PROTOTYPE ABOVE THIS LINE----
//----DO NOT MODIFY THE CODE BELOW THIS LINE----

void modify_grocery_list() {
    
    //----DO NOT MODIFY THE CODE ABOVE THIS LINE----
    //----WRITE YOUR FUNCTION CALLS BELOW THIS LINE----


    print_grocery_list(); 
    print_grocery_list(5); 
    print_grocery_list(7,11);   
    //----WRITE YOUR FUNCTION CALLS ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
}

void print_grocery_list(int apples, int oranges, int mangos) { //----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES
                                     //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    cout << apples << " apples" << "\n" 
	    << oranges << " oranges" << "\n" 
	    << mangos << " mangos" << "\n";
}

int main(){
    modify_grocery_list();
}
```

