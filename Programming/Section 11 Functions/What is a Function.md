# C++ Programs

- C++ Standard Libraries (functions and classes)
- Third-party Libraries (functions and classes)
- Our own functions and classes

# Functions allow the modularization of a program

- Separate code into logical self-contained units
- These units can be reused

# Modularized Code:

How we have been writing code:
```cpp
int main() {
// Read Input
	statement1;
	statement2;
	statement3;
	statement4;

// Process Input
	statement5;
	statement6;
	statement7;

// Provide Output
	statement8;
	statement9;
	statement10;

	return 0;
}
```

Modularized Code:
```cpp
int main() {
// Read Input
	read_input();

// Process Input
	process_input();

// Provide Output
	provide_output();
}
```

 In the first example you can see how we have been writing code up to this point. Lot's of statements after one another, some of these statements might be if statements, some might be looping statements but you can see that this program has 3 logical sections. One for input, one for processing and one for output but everything is placed int the `main` function. This is okay for relatively small programs like the ones we have written.   


# Coding Exercise 22::
Using Functions from the cmath Library

In this exercise you will create a program that will be used as a POS (Point of Sale) system in a restaurant. The `bill_total` is given as well as the `number_of_guests`. The 5 guests will be splitting the bill evenly and so the `individual_bill` will be `bill_total` / `number_of_guests`. The POS will be used in three different locations, each with different guidelines for printing bills.

At location 1, `individual_bill_1` always rounds down to the nearest dollar.

At location 2, `individual_bill_2` always rounds to the nearest dollar.

At location 3, `individual_bill_3` always rounds up to the nearest cent.

Determine what the `individual_bill` will be at each of the locations.

Begin by declaring and initializing `individual_bill`.

Now, declare and initialize `individual_bill_1` by using the `<cmath>` function `floor` with `individual_bill` as the argument.

Next, declare and initialize `individual_bill_2` by using the `<cmath>` function `round` with `individual_bill` as the argument.

Finally, declare and initialize `individual_bill_3` by using the `<cmath>` function `ceil` with `individual_bill` as the argument. In order to round `individual_bill_3` to the nearest cent, you must `multiply the argument` of the function `ceil` by `100` and then `divide the result` of the function by `100`.

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <iostream>
#include <cmath>
using namespace std;

void c_math_functions() {
    double bill_total {102.78};
    int number_of_guests {5};
    
    //DO NOT MODIFY THE CODE ABOVE THIS LINE----
    //----WRITE YOUR CODE BELOW THIS LINE----
    
    
    
    //----WRITE YOUR CODE ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    cout << "The individual bill at location 1 will be $" 
    << individual_bill_1 << "\n" 
    << "The individual bill at location 2 will be $" 
    << individual_bill_2 << "\n" 
    << "The individual bill at location 3 will be $" 
    << individual_bill_3;
}
```
## My solution:

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    double bill_total{102.78};
    int number_of_guests {5};
    double individual_bill = bill_total/number_of_guests;

    int individual_bill_1 = floor(individual_bill);
    int individual_bill_2 = round(individual_bill);
    double individual_bill_3 = ceil(individual_bill*100)/100; 
    //Turning the argument into a large integer and then bringing
    //Bringing it back down to the correct float size

    cout << "The individual bill at location 1 will be $" 
    << individual_bill_1 << "\n" 
    << "The individual bill at location 2 will be $" 
    << individual_bill_2 << "\n" 
    << "The individual bill at location 3 will be $" 
    << individual_bill_3;
}
```
