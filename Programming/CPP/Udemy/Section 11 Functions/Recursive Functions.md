# Introduction

- A recursive function is a function that calls itself.
	- Either directly or indirectly through function

- Recursive Problem Solving
	- Base Case
	- Divide the rest of Problem into Subproblem and do Recursive Solutions

- There are Many Problems that Lend Themselves to Recursive Solutions.

- Mathematical - Factorial, Fibonacci, Fractals, etc.

 - Searching and Sorting - Binary Search, Search Trees, etc.

# Example: Factorials

Here's a quick catch-up lesson on [Factorials](../../../../Math/Factorials.md).

```
0! = 1
n! = n * (n-1)!
```

- Base Case:
	- factorial(0) = 1

- Recursive Case:
	- factorial(n) = n * factorial(n-1)

```cpp
unsigned long long factorial(unsigned long long n){
	if (n == 0){
		return 1;                // base case
	}
	return n * factorial (n-1);  // recursive case
}

int main(){
	cout << factorial(8) << endl; // 40320
	return 0;
}
```

So let's look at the code starting at `main()`, we call `factorial()` and pass in an 8 to the `factorial()` function. When the `factorial()` function returns, the value returned will be output to the console. In this case we expect 40320. 

Let's look at the factorial function. First we need to decide which types we'll except and return. The `factorial()` function can generate massively huge numbers, so in this case we're using unsigned long long as the return type and the parameter type. This can hold very very large positive integers but we can still get an overflow even with such a big number. 

If you look at the code for the factorial function it looks exactly like the mathematical definition of factorial. We check a base case, in this case if `n` is equal to zero we return 1. Remember, the `return` knocks you out of the function immediately. Otherwise we return the result of calling the `factorial()` function with `n-1`. So in this case it would be `return` `n` times call `factorial()` with `n-1`. There's the recursion, the base case is super important since it's what stops the recursion, otherwise we'd recurse indefinitely and eventually we'd run out of stack space and get a stack overflow error. 

Let's look at calculating a Fibonacci number.

# Example: Fibonacci Number

Need a refresher? Read through this revision of [Fibonacci Numbers](../../../../Math/Fibonacci%20Numbers.md).

```
Fib (0) = 0
Fib (1) = 1
Fib (n) = Fib(n-1) + Fib(n-2)
```

- Base Case:
	- Fib(0) = 0
	- Fib(1) = 1

- Recursive Case:
	- Fib(n) = Fib(n-1) + Fib(n-2)

# In the IDE:

```cpp
#include <iostream>

using namespace std;

unsigned long long fibonacci (unsigned long long n){
	if (n <= 1){
		return n;        // base cases
	}
	return fibonacci(n-1) + fibonacci(n-2); // recursion
}

int main(){
	cout << fibonacci(30) << endl; // 832040
	return 0;
}
```

Again, we're using unsigned long long in this case since Fibonacci can also produce huge numbers. Notice in the `main()` function we call `fibonacci()` and the result we expect back is `832040`.

Now let's look at the `fibonacci()` function, notice that in the **base case** if `n` is less than or equal to `1` then we simply return `n`. So when `n` is `0` we return `0` and when `n` is `1` we return `1`. That handles both **base cases** in one step. We can easily rewrite this condition to explicitly check `n=0` and `n=1` but this achieves the same result. This base case is what stops the recursion, if `n` not `0` or `1` then we call `fibonacci()` again with both pieces of the problem definition. Eventually the recursion will stop and the result will be returned to `main()`. 

Notice how much the code looks exactly like the mathematical definition of Fibonacci. This is by design, let's look at a few thoughts on recursion:
# Important Notes:

- If a recursion doesn't eventually stop you will have infinite recursion.

- Recursion can be resource intensive.

- Remember the base case(s).
	- They terminate the recursion.

- Only use recursive solutions when it makes sense.

- Anything that can be done recursively can be done iteratively.
	- Stack overflow error.

# Example 1: Factorial Visualized

Building up the stack for line 5 till the base case:

![](Pictures/Recursive%20Functions%20-%20Factorial%20Visualized.png)

Once we reach that point every stack is popped off one by one returning it's value:

![](Pictures/Recursive%20Functions%20-%20First%20Stack%20Popped%20Off.png)

![](Pictures/Recursive%20Functions%20-%20Second%20Function.png)

![](Pictures/Recursive%20Functions%20-%20Final%20Stack%20Popped%20Off.png)

# Section Challenge:

Improve the Section Challenge of Section 9 using Functions.

## My Solution:

```cpp
// Section 11
#include <iostream>
#include <vector>
#include <string>

using namespace std;

const string print_options();
string print_numbers(const vector<int> &num);
inline void add_numbers(vector<int> &num, char &opt);
double mean_number(const vector<int> &num);
int smallest_number(const vector<int> &num);
int largest_number(const vector<int> &num);

int main(){
    vector<int> numbers{};
    char opt{};

    do {
        cout << print_options();
        cin >> opt;

        switch (tolower(opt)) {
            case 'p': {
                cout << print_numbers(numbers);
                break;
            }
            case 'a': {
                add_numbers(numbers,opt);
                break;
            }
            case 'm': {
                if (numbers.empty()){
                    cout << "No numbers to mean\n";
                } else {
                    cout << "The average is: " + to_string(mean_number(numbers)) + "\n";
                }
                break;
            }
            case 's': {
                if (numbers.empty()) {
                    cout << "No numbers to display smallest.\n";
                } else {
                    cout << "The smallest number is: " 
                        << to_string(smallest_number(numbers)) + "\n";
                }
                break;
            }
            case 'l': {
                if (numbers.empty()) {
                    cout << "No numbers to display largest.\n";
                } else {
                    cout << "The largest number is: " 
                        << to_string(largest_number(numbers)) + "\n";
                }
                break;
            }
            case 'q':
                cout << "Goodbye\n";
                break;
            default:
                cout << "Unknown selection, please try again";
        }
    } while (opt != 'Q' && opt != 'q');
}

const string print_options(){
    const string options{
        "-------------------------------\n"
        "P - Print numbers\n"
        "A - Add a number\n"
        "M - Display mean of the numbers\n"
        "S - Display the smallest number\n"
        "L - Display the largest number\n"
        "Q - Quit\n"
    };
    return options;
}

string print_numbers(const vector<int> &num){
    string numbers{};
    if (num.empty()){
        numbers = "[] - No numbers to display.";
    } else {
        for (auto i:num){
            numbers += to_string(i) + " ";
        }
    }
    return numbers + "\n";
}

inline void add_numbers(vector<int> &num, char &opt){
    int num_to_add{};
        do {
            cout << "What number would you like to add?: \n";
            cin >> num_to_add;
            num.push_back(num_to_add);
            cout << "Would you like to add another number? (Y/N)\n";
            cin >> opt;
        } while (opt != 'n' && opt != 'N');
}

double mean_number(const vector<int> &num){
    int total{};
    for (auto i:num) total += i;
    return static_cast<double>(total) / num.size();
}

int smallest_number(const vector<int> &num){
    int smallest = num.at(0);
    for (auto i:num){
        if (smallest > i){
            smallest = i;
        }
    }
    return smallest;
}

int largest_number(const vector<int> &num){
    int largest = num.at(0);
    for (auto i:num){
        if (largest < i){
            largest = i;
        }
    }
    return largest;
}

```

## Instructor Solution:

```cpp
>
#include <vector>
using namespace std;

// Prototypes for displaying the menu and getting use selection
void display_menu();
char get_selection();

// Menu handling function prototypes
void handle_display(const vector <int> &v);
void handle_add(vector<int> &v);
void handle_mean(const vector <int> &v);
void handle_smallest(const vector <int> &v);
void handle_largest(const vector <int> &v);
void handle_find(const vector <int> &v);
void handle_quit();
void handle_unknown();

// Prototypes for functons that work with the list.
// To display it calculate mean,etc
void display_list(const vector<int> &v);
double calculate_mean(const vector<int> &v);
int get_smallest(const vector<int> &v);
int get_largest(const vector<int> &v);
bool find(const vector<int> &v, int target);

int main(){
	vector<int> numbers;
	char selection{};

	do {
		display_menu();
		selection = get_selection();
		switch(selection){
			case 'P':
				handle_display(numbers);
				break;
			case 'A':
				handle_add(numbers);
				break;
			case 'M':
				handle_mean(numbers);
				break;
			case 'S':
				handle_smallest(numbers);
				break;
			case 'L':
				handle_largest(numbers);
				break;
			case 'F':
				handle_find(numbers);
				break;
			case 'Q':
				handle_quit();
				break;
			default:
				handle_unknown();
                }
	} while (selection != 'Q');
	cout << endl;
	return 0;
}

/**************************************************
This function displays the menu to the console
**************************************************/

void display_menu(){
	cout << "\nP - Print numbers" << endl;
	cout << "A - Add a number" << endl;
	cout << "M - Display mean of the numbers" << endl;
	cout << "S - Display the smallest number" << endl;
	cout << "L - Display the largest number" << endl;
	cout << "F - Find Number" << endl;
	cout << "Q - Quit" << endl;
	cout << "\nEnter your choice: ";
}

/**************************************************
This function simply reads a character selecdtion from
stdin and returns it as upper case.
**************************************************/

char get_selection(){
	char selection {};
	cin >> selection;
	return toupper(selection);
}

/**************************************************
This function is called when the user selects the 
display list option from the main menu.
Note that the parameter is a const reference parameter.
This function should NOT modify the list of numbers.
**************************************************/

void handle_display(const vector <int> &v){
	if (v.size() == 0)
		cout << "[] - the list is empty" << endl;
	else
		display_list(v);
}

/*************************************************
This function is called when the user selects add a
to the list from the main menu.
Note that the vector parameter must NOT be const
since it will be changing the list of numbers.
**************************************************/

void handle_add(vector<int> &v){
	int num_to_add{};
	cout << "Enter an integer to add to the list: ";
	cin >> num_to_add;
	v.push_back(num_to_add);
	cout << num_to_add << " added" << endl;
}

/**************************************************
This function is called when the user selects calculate
the mean from the main menu.
Note that the parameter is a const reference parameter.
This function should NOT modify the list of numbers.
**************************************************/

void handle_mean(const vector <int> &v){
	if (v.size() == 0)
		cout << "Unable to calculate the mean - list is empty"
			<< endl;
	else
		cout << "The mean is " << calculate_mean(v) << endl;
}

/**************************************************
This function is called when the user selects the 
display smallest option from the menu.
**************************************************/

void handle_smallest(const vector <int> &v){
	if (v.size() == 0)
		cout << "Unable to display smallest - list is empty"
			<< endl;
	else
		cout << "The smallest number is " << get_smallest(v)
			<< endl;
}

/**************************************************
This function is called when the user selects the 
display largest option from the menu.
**************************************************/

void handle_largest(const vector <int> &v){
	if (v.size() == 0)
		cout << "Unable to display largest - list is empty"
			<< endl;
	else
		cout << "The largest number is " << get_largest(v)
			<< endl;
}

/**************************************************
This function is called when the user selects the find
option from the main menu.
**************************************************/

void handle_find(const vector <int> &v){
	int target{};
	cout << "Enter the number to find: ";
	cin >> target;
	if (find(v,target))
		cout << target << " was found";
	else
		cout << target << " was not found"
			<< endl;
}

/**************************************************
This function is called when the user selects the quit
option from the main menu.
**************************************************/

void handle_quit(){
	cout << "Goodbye" << endl;
}

/**************************************************
This function is called whenever the user enters a selection and we don't know how to handle it.
**************************************************/

void handle_unknown(){
	cout << "Unknown selection - try again" << endl;
}

/**************************************************
This function expects a list of integers as a vector 
and displays all the integers in the list in square brackets.
Note that the parameter is a const reference parameter.
This function shuld NOT modify the list of numbers.
**************************************************/

void display_list(const vector<int> &v){
	cout << "[ ";
	for (auto num:v)
		cout << num << " ";
	cout << "]" << endl;
}

/**************************************************
This function expects a list of integers as a vector
and returns the calculated mean.
Note that the parameter is a const reference parameter.
This function should NOT modify the list of numbers.
Note: The list must not be empty.
**************************************************/

double calculate_mean(const vector<int> &v){
	int total{};
	for (auto num:v)
		total += num;
	return static_cast<double>(total)/v.size();
}

/**************************************************
This function expects a list of integers as a vector
and returns the smallest number.
Note that the parameter is a const reference parameter.
This function should NOT modify the list of numbers.
Note: The list must not be empty.
**************************************************/

int get_smallest(const vector<int> &v){
	int smallest = v.at(0);
	for (auto num:v)
		if (smallest > num)
			smallest = num;
	return smallest;
}

/**************************************************
This function expects a list of integers as a vector
and returns the largest number.
Note that the parameter is a const reference parameter.
This function should NOT modify the list of numbers.
Note: The list must not be empty.
**************************************************/

int get_largest(const vector<int> &v){
	int largest = v.at(0);
	for (auto num:v)
		if (largest < num)
			largest = num;
	return largest;
}

/**************************************************
This function expects a list of integers as a vector
and returns true or false depending on wheter or not
the second integer passed in was found in the vector.
Note that the parameter is a const reference parameter.
This function should NOT modify the list of numbers.
Note: The list must not be empty.
**************************************************/

bool find(const vector<int> &v, int target){
	for (auto num:v)
		if (num == target)
			return true;
	return false;
}
```