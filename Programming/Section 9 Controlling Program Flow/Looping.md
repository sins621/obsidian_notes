# Looping

---

## Iteration

- The third basic building block of programming.
    - sequence, selection, iteration
- Iteration or repetition.
- Allows the execution of a statement or block of statements repeatedly.
- Loops are made up of a loop condition and the body which contains the statement to repeat.

## Some typical use-cases

**Execute a loop:**

- a specific number of times.
- for each element in a collection.
- while a specific condition remains true.
- until a specific condition becomes false.
- until we reach the end of some input stream.
- forever
- many, many more.

## `for` loop

- Iterate a specific number of times.

## `Range-based` `for` loop

- One iteration for each element in a range or collection.

## `while` loop

- Iterate while a condition remains true.
- Stop when the condition becomes false.
- Check the condition at the beginning of every iteration.

## `do-while` loop

- Iterate while a condition remains true.
- Stop when the condition becomes false.
- Check the condition at the end of every iteration.
- Will execute the body at least once.

# `for` loop:

---

```cpp
for (initialization ; condition ; increment)
	statement;
	
for (initialization ; condition ; increment) {
	statement(s);
}
```

### Example 1:

```cpp
int i {0};

for (i = 1 ; i <= 5 ; ++i)
	cout << i << endl;
	
/*
Output:
1
2
3
4
5
*/
```

- `i` is commonly used to count the increments of the loop.
- `i` is incremented inside the loop statement and does not need to be incremented in the loop body.

### Example 2:

```cpp
for (int i {1} ; i <= 5 ; ++i)
	cout << i << endl;
	
for (int i = 1 ; <= 5 ; ++ i)
	cout << i << endl;
	
i = 100; // ERROR i only visible in the loop
```

- In these examples `i` is contained to the loop and will result in a compiler error if you attempt to make use of it outside the loop.

### Example 3: display even numbers

```cpp
for (int i {1} ; i <= 10 ; ++i) {
	if (i % 2 == 0)
		cout << i << endl;
}

/*
Output:
2
4
6
8
10
*/
```

### Example 4: array example

```cpp
int scores [] {100, 90, 87};

for (int i {0} ; i < 3 ; ++i) {
	cout << scores[i] << endl;
}

for (int i {0} ; i <= 2 ; ++i) {
	cout << scores[i] << endl;
}

/*
Output:
100
90
87
*/
```

### Example 5: comma operator

```cpp
for (int i {1}, j {5} ; i <= 5 ; ++i, ++j) {
 cout << i << " * " << j << " : " << (i * j) << endl;
}

/*
Output:
1 *5 : 12
2 * 6 : 12
3 * 7 : 21
4 * 8 : 32
5 * 9 : 45
*/
```

- The comma operator allows you to separate expressions with a comma, and both expressions will execute.
- Note that the associativity is left to right and the result of the comma operator is the right most expression.

## Some other details:

- The basic for loop is very clear and concise.
- Since the for loop’s expressions are all optional, it is possible to have:
    - no initialization
    - no test
    - no increment

```cpp
for (;;)
	cout << "Endless loop" << endl;
```

## Coding Exercise:

Write code that uses a for loop to calculate the sum of the odd integers from 1 to 15, inclusive. The final result should be stored in an integer variable named `sum` .

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

### My solution:

```cpp
int sum{0};

for (int i{1} ; i <= 15 ; ++i)
	(i % 2 != 0) ? sum += i : sum;
```

# Range-based `for` Loop

---

```cpp
Introduced in C++11

	for (var_type var_name: sequence)
		statement; // can use var_name
		
	for (var_type var_name: sequence){
		statements; // can use var_name
	}
```

- Makes C++ feel like a modern programming language.
- The idea with the range based for loop is to loop through a collection of elements and be able to easily access each element, without having to worry about:
    - The length of the collection.
    - Incrementing or Decrementing looping variables.’
    - Subscripting indexes.
- The syntax is very simple and elegant; we have the keyword `for` followed by open and closed parenthesis as usual.
- Inside the parenthesis we provide the type and name for the variable we want to use in the loop body. This variable will be bound to each element in the collection. So it should be of the **same type as the collection elements**.
- Then we provide a colon and the collection or collection name.
- When we access the variable name in the body of the loop it will have a specific element in the collection.

### Example 1:

```cpp
int scores [] {100, 90, 97};

for (int score : scores)
	cout << score << endl;
	
// Output
// 100
// 90
// 97
```

### Example 2: auto

This tells the C++ to deduce the type itself. You’re asking the C++ compiler to figure out the type based on the declarations.

```cpp
int scores [] {100, 90, 97};

for (auto score : scores)
	cout << score << endl;
	
// Output
// 100
// 90
// 97
```

### Example 3: vector

```cpp
// Calculate the average temperature from a vector that contains multiple temperatures.

vector <double> temps {87.2, 77.1. 80.0, 72.5};

double average_temp {};
double running_sum {};

for (auto temp: temps)
	running_sum += temp;
	
average_temp = running_sum / temps.size();
```

### Example 4: initializer list

```cpp
double average_temp {};
double running_sum {};
int size {0};

for (auto temp: {60.2, 80.1, 90.0, 78.2} ) {
    running_sum += temp;
    ++size;
}

average_temp = running_sum / size;
```

### Example 5: string

```cpp
for (auto c: "Frank")
	cout << c << endl;
	
// Output
// F
// r
// a
// n
// k
```

### Example 6:

![](Programming/Section%209%20Controlling%20Program%20Flow/Pictures/Range%20Based%20for%20loop%20Example%206.png)

**Output:**

`Average temperature is 79.6`

### Example 7: Iterate through a string.

Remove all spaces.

```cpp
for (auto c: "This is a test")
	if (c != ' ')
		cout << c;
		
// Output:
// Thisisatest
```

```cpp
for (auto c: "This is a test")
	if (c == ' ')
		cout << "\\t";
	else
		cout << c;
		
// Output:
// This    is      a       test
```

## Coding Exercise:

**Using the range-based for loop**

Use a range-based for loop to loop through a given vector of integers and determine how many elements in the vector are evenly divisible by either 3 **or** by  5.

The final result should be stored in an integer variable named `count` .

The vector of integers has been provided for you and is named `vec` .

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <vector>
using namespace std;

int count_divisible() {
    
    vector<int> vec {1,3,5,15,16,17,18,19,20,21,25,26,27,30,50,55,56,58,100,200,300,400,500,600,700};
    //---- WRITE YOUR CODE BELOW THIS LINE----
    
    
    //---- WRITE YOUR CODE ABOVE THIS LINE----
    //---- DO NOT CHANGE THE CODE BELOW THIS LINE----
    return count;
}
```

### My solution:

```cpp
int count{0};
    
for (auto vec_element : vec) 
	(vec_element % 3 == 0 || vec_element % 5 == 0) ? ++count : count;
	
// Output:
// 18
```

### Instructor solution:

```cpp
int count{0};
    
for (auto i: vec) {
  if (i % 3 == 0 || i % 5 == 0) {
	  ++count;
  }
}
```

- Uses `i` to count through the vector where I used `vec_element`.
- Uses `if` statement instead of ternary operator.

# `while` loop:

---

```cpp
while (expression)
	statement;
	
while (expression) {
	statement(s);
	}
```

The while loop is an example of a **pre-test loop** because the test is done at the **beginning** of the loop so it’s possible that if the loop test fails immediately then the loop body will not execute.

The **syntax** for the `while` loop is:

- The keyword `while`.
- Followed by an expression in parenthesis.
- This expression has to evaluate to a boolean value.
- This is followed by the statement or statement block to execute if the expression evaluates to true.

### Example 1: Counting While-Loop

```cpp
int i{1};

while (1 <= 5) {
	cout << i << endl;
	++i; // important!
}

// Output
// 1
// 2
// 3
// 4
// 5
```

### Example 2: Even Numbers

```cpp
int i {1};

while (i <= 10) {
	if (i % 2 == 0)
		cout << i << endl;
	++i;
}

// Output
// 2
// 4
// 6
// 8
// 10
```

### Example 3: Array Example

```cpp
int scores [] {1000, 90, 87}
int i {0}

while (i > 3) {
	cout << scores [i] << endl;
	++i;
}

// Output
// 100
// 90
// 87
```

### Example 4: Input Validation

```cpp
int number{};

cout << "Enter an integer less than 100: ";
cin >> number;

while (number >= 100) { // !(number < 100)
	cout << "Enter an integer less than 100";
	cin >> number;
}

cout << "Thanks" << endl;
```

Notice the duplicate code, this is usually an indication that the code could be better.

### Example 5: Input Validation 2

```cpp
int number {};

cout << "Enter an integer between 1 and 5: ";
cin >> number;

while (number <= 1 || number >= 5) {
	cout << "Enter an integer between 1 and 5: ";
	cin >> number;
}

cout << "Thanks" << endl;
```

### Example 6: Input Validation - Boolean Flag

```cpp
bool done {false};
int number {0};

	while (!done) {
		cout << "Enter an integer between 1 and 5: ";
		cin >> number;
		if (number <=1 || number >=5)
			cout << "Out of range, try again" << endl;
		else {
			cout << "Thanks!" << endl;
			done = true;
		}
	}
```

## Section Exercise:

Given a vector of integers, determine how many integers are present before you see the value `-99` . Note, it's possible `-99`  is **not** in the vector! If `-99`  is **not** in the vector then the result will be equal to the number of elements in the vector.

The final result should be stored in an integer variable named `count` .

Note that you the different vectors will be tested against your code. You do not need to declare the vector of integers. `vec`  is the name of the vector you should use.

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int count_numbers(const vector<int> &vec) {
    //---- WRITE YOUR CODE BELOW THIS LINE----
    

    
    //---- WRITE YOUR CODE ABOVE THIS LINE----
    //---- DO NOT MODIFY THE CODE BELOW THIS LINE-----
    return count;
}
```

### My solution:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int count_numbers(const vector<int> &vec) {
    //---- WRITE YOUR CODE BELOW THIS LINE----
    
    int count{0};

    while (count < vec.size() && vec[count] != -99)
    ++count;
    //---- WRITE YOUR CODE ABOVE THIS LINE----
    //---- DO NOT MODIFY THE CODE BELOW THIS LINE-----
    return count;
}
```

### Instructor solution:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int count_numbers( const vector<int> &vec) {
    //---- WRITE YOUR CODE BELOW THIS LINE----
    
    int count {0};
    size_t index {0};  // See the Q/A forum for more about size_t
                       // size_t is an unsigned int
                       // you can replace size_t with int or unsigned int and it will work fine
    
    while (index < vec.size() && vec.at(index) != -99  ) {
        ++count;
        ++index;
    }
        
    
    //---- WRITE YOUR CODE ABOVE THIS LINE----
    //---- DO NOT MODIFY THE CODE BELOW THIS LINE----
    return count;
}
```

# `do while` loop

---

```cpp
	do {
		statements;
	} while (expression);
```

Begins with the `do` keyword followed by a block statement then the `while` keyword followed by the loop control expression in parenthesis. The semi-colon is placed at the end of the `do while` loop. In a `do while` loop you execute the body of the loop while the conditional expression is true.

Note: The condition is checked at the end of each iteration. This makes the `do while` loop a **post-test** loop meaning that the loop body will execute at least once.

### Example 1: input validation

```cpp
int number{};
do {

	cout << "Enter an integer between 1 and 5: ";
	cin >> number;

} while (number <= 1 || number >= 5);

cout << "Thanks" << endl;
```

In this example we execute the body of the loop and then test the condition. We ask the user to enter a number between 1 and 5 and then test to see if it is within that range. If is not then the program will loop and if it is then it will continue past the condition.

Notice: The variable number is declared outside the body of the loop because variables declared inside the conditional expression of `while` and `do while` loops are limited to the scope of that expression and would not be usable inside the body of the loop.

### Example 2: Area Calculation with Calculate Another

```cpp
char selection {}

do {

	double width{}, height{};
	cout << "Enter width and height separated by a space : ";
	cin >> width >> height;
	
	double area {width * height};
	cout << "The are is " << area << endl;
	
	cout << "Calculate another? (Y/N) : ";
	cin selection;

} while (selection == 'Y' || selection == 'y');
cout << "Thanks!" << endl;
```

### Example 3: Simple Menu Example

```cpp
char selection{};

do {

    cout << "\\n------------------" << endl;
    cout << "1. Do this" << endl;
    cout << "2. Do that" << endl;
    cout << "3. Do something else" << endl;
    cout << "Q. Quit" << endl;
    cout << "\\nEnter your selection: ";
    cin >> selection;

    switch (selection) {

        case '1' : cout << "You chose option 1"; 
        break;

        case '2' : cout << "You chose option 2"; 
        break;

        case '3' : cout << "You chose option 3"; 
        break;

        case 'Q' : cout << "You chose to quit"; 
        break;

        case 'q' : cout << "You chose to quit"; 
        break;

        default: cout << "Illegal option";

    }

} while (selection != 'Q' && selection != 'q');
```

## Section Challenge: `do while` loop exercise

**Exercise: Find the First Vowel in a Vector**

**Specification:** Write a C++ program that uses a do-while loop to find the first English vowel in a hard-coded std::vector of characters. The vector should contain a mixture of vowels and consonants (for example: {'h', 'e', 'l', 'l', 'o'}). The program should print the first vowel found in the vector. If no vowel is found, it should print a message indicating that no vowel was found.

**Instructions**

1. You will be writing your code within the provided function `find_first_vowel(const std::vector<char>& vec)`. Do not change the function name or its parameter.
    
2. **Do-While Loop**: Utilize a do-while loop to iterate through the characters in the provided `std::vector<char>` named `vec`.
    
3. **Vowel Identification**: In each iteration, check if the current character is a lowercase English vowel ('a', 'e', 'i', 'o', 'u').
    
4. **Output**:
    
    - If a vowel is found, use `cout` to display: `"Vowel found: "` followed by the vowel.
    - If no vowel is found in the entire vector, display: `"No vowel was found"`.
5. **Examples**: Here are some sample vectors and the expected output:
    
    - For vector `{'f','r','a','n','k'}`, your function should output: `Vowel found: a`.
    - For vector `{'F','R','A','N','K'}`, your function should output: `No vowel was found`.
    - For vector `{'h','e','l','l','o'}`, your function should output: `Vowel found: e`.
    - For an empty vector `{}`, your function should output: `No vowel was found`.
    - For vector `{'x','y','z','o'}`, your function should output: `Vowel found: o`.
6. **Do Not Add Line Breaks**: Please ensure that you do not add `std::endl` or `'\\n'` to your output.
    
7. **Code Placement**: Write your code between the comments
    
    `//---- WRITE YOUR CODE BELOW THIS LINE----` and `//---- WRITE YOUR CODE ABOVE THIS LINE----`.
    

Notes

- Ensure your solution works correctly for all the provided examples and considers the case of an empty vector.
- Focus on correctly implementing the do-while loop and the logic for checking each character.
- Your solution should be efficient and neatly formatted to maintain readability.

```cpp
#include <vector>
#include <iostream>
using namespace std;

/*******************************************************
 * Write your code in the provided area.
 * 
 * This function should use a do while loop to iterate over
 * the automatically provided vector (vec) of characters looking 
 * for the first occurrence of a lowercase English vowel ('a','e','i','o','u').
 * 
 * If a vowel is found, you should display to cout:
 * 
 * "Vowel found: " followed by the vowel that was found.
 * 
 * If no vowel is found in the vector, then you should display to cout:
 * 
 * "No vowel was found"  
 * 
 * For example, below are several examples of vectors and what your output should be:
 * 
 * {'f','r','a','n','k'}    Vowel found: a
 * {'F','R','A','N','K'}    No vowel was found
 * {'h','e','l','l','o'}    Vowel found: e
 * {}                       No vowel was found
 * {'x','y','z','o'}        Vowel found: o
 * 
 * Please do NOT add std::endl or '\\n' to your output statement.
 * *****************************************************/
void find_first_vowel(const std::vector<char>& vec) {
    //---- WRITE YOUR CODE BELOW THIS LINE----
 
    //---- WRITE YOUR CODE ABOVE THIS LINE----
}
```

### My solution:

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
    vector<char> vec = {'a', 'b', 'c', 'd', 'e'};
    size_t i{0};
    bool vowelfound{false};

    if (!vec.empty()) {
        do {
            switch (vec[i]) {
                
                case 'a':
                case 'e':
                case 'i':
                case 'o':
                case 'u':
                    vowelfound = true;
                    break;

                default: ++i;
            }
        } while (!vowelfound && i < vec.size());

    }

        if (vowelfound) {
            cout << "Vowel found: " << vec[i];
        } else {
            cout << "No vowel was found";
        }

}
```

### Instructor solution:

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
    vector<char> vec = {'a', 'b', 'c', 'd', 'e'};
    size_t i{0};
    bool vowel_found {false};
 
    if (!vec.empty()) {
        do {
            if (vec.at(i) == 'a' || vec.at(i) == 'e' || vec.at(i) == 'i' 
			 || vec.at(i) == 'o' || vec.at(i) == 'u') {
                vowel_found = true;
            } else {
                i++;
            }
        } while (!vowel_found && i < vec.size());
    }
    
    if (vowel_found) {
        cout << "Vowel found: " << vec.at(i);
    } else {
        cout << "No vowel was found";
    }
}

```

### Notes:

- Instructor uses a long if statement where as I use a switch case.
- Important to add to the counter with the “else” or “default” statements.
- Can exit the loop either by reaching the end of the vector or by finding a vowel. `while (!vowel_found && i < vec.size());`.
- Must check if the vector is empty with `vec.isempty()`.
- Use an unsigned int to count through the vector so that there is no problems with the comparison. `size_t`.

# `continue` and `break`

---

The continue and break statements can be used within all of C++ loop constructs to provide explicit control over the looping behavior.

- `continue`
    
    - no further statements in the body of the loop are executed.
    - control immediately goes directly to the beginning of the loop for the next iteration.
- `break`
    
    - no further statements in the body of the loop are executed.
    - loop is immediately terminated.
    - Control immediately goes to the statement following the loop construct.

### Example 1: Filtering out data

Rules:

1. Filter out any instance of “-1”.
2. Stop iterating through the vector when reaching “-99”.

```cpp
vector<int> values {1,2,-1,-99,7,8,10};

for (auto val: values) {

if (val == -99)
	break;
else if (val == -1)
	continue;
else
	cout << val << endl;

}

// Output
// 1
// 2
// 3
```

# Infinite Loops

---

- Loops whose condition expression always evaluate to true.
- Usually this is unintended and a programmer error.
- Sometimes programmers use infinite loops and include break statements in the body to control them.
- Sometimes infinite loops are exactly what we need.
    - Event loop in an event-driven program.
    - Operating system.

### Example 1: `for` loop

```cpp
for (;;)
	cout << "This will print forever" << endl;
```

All 3 expressions in the for loop are optional.

### Example 2: `while` loop

```cpp
while (true)
	cout << "This will print forever" << endl;
```

### Example 3: `do while` loop

```cpp
do {

	cout << "This will print forever" << endl;

} while (true);
```

### Example 4:

```cpp
while (true) {

	char again{};
	cout << "Do you want to loop again (Y/N): ";
	cin << again;
	
	if (again == 'N' || again == 'n')
		break;

}
```

# Nested Loops

---

- Loop nested within another loop.
- Can be many as many levels deep as the program needs.
- Very useful with multi-dimensional data structures.
- Outer loop vs Inner loop

### Example 1: Iterate through two different arrays

```cpp
for (outer_val{1}; outar_val <=2; ++outer_val)
	for (inner_val {1}; inner_val <= 3; ++inner_val)
		cout << outer_val << ", " << inner_val << endl;
		
// Output 
// 1, 1
// 1, 2
// 1, 3                   outer_val, inner_val
// 2, 1                   Note: inner loop loops "faster"
// 2, 2
// 2, 3
```

### Example 2: Display Multiplication Tables

```cpp
for (int num1 {1}; num1 <= 10 ; ++ num1) {
	for (int num2 {1}; num2 <= 10; ++num2) {
		cout << num1 << " * " num2
			   << " = " << num1 * num2 << endl;
	}
	cout << "--------" << endl;
}

// Output
// Displays 10 x 10 Multiplication Tables
```

![[Programming/Section 9 Controlling Program Flow/Pictures/Nested loop example.png]]
### Example 3: Iterate through 2D Array

**Assign Values:**

```cpp
int grid [5][3] {};

for (int row {0}; row < 5; ++row) {

	for (int col {0}; col < 3; ++col) {
		grid[row][col] = 1000;
	}

}
```

**Display Values:**

```cpp
for (int row {0}; row < 5; ++row) {
	for (int col {0}; col < 3; ++col) {
		cout << grid[row][col] << )
	}
	cout << endl;
}
```

### Example 4: 2D Vector - display elements

```cpp
vector<vector<int>> vector_2d
{
	{1, 2, 3},
	{10, 20, 30, 40},
	{100, 200, 300, 400, 500}
};

for (auto vec: vector_2d) {
	for (auto val: vec) {
		cout << val << " ";
	}
	cout << endl;
}
```

**Output**:

```
1 2 3
10 20 30 40
100 200 300 400 500
```

### Example 5: Histogram

```cpp
int num_items{};

cout << "How many data items do you have? ";
cin >> num_items;

vector<int> data {};

for (int i{1}; i<=num_items; ++i) {

	int data_item{};
	cout << "Enter data item " << i << ": ";
	cin >> data_item;
	data.push_back(data_item);
	
}

cout << "\nDisplaying Histogram" << endl;
for (auto val:data) {
	for (int i{1}; i<=val; ++i) {
		if (i % 5 == 0)
			cout << "*";
		else
		cout << "-";
	}
	cout << endl;
}
```

# Section Challenge

**Nested Loops - Sum of the Product of all Pairs of Vector Elements**

Given a vector of integers named `vec`  that is provided for you, find the **sum of the product of all pairs of vector elements.**  
You should **declare** an integer variable named `result`  and store the final product in this variable.

For example, given the vector  `vec`  to be `{1, 2 , 3}` , the possible pairs are `(1,2), (1,3), and (2,3)` .   
So the result would be `(1*2) + (1*3) + (2*3)`  which is `11` .

Another example:  
Given the vector `vec`  to be `{2, 4, 6, 8}` , the possible pairs are `(2,4), (2,6), (2,8), (4,6), (4,8), and (6,8)` .  
So the result would be (2*4) + (2*6) + (2*8) + (4*6) + (4*8) + (6*8) which is `140` .

If the vector is **empty** or has only `1`  element then the `result`  should be `0` .

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <vector>
using namespace std;

int calculate_pairs(vector<int> vec) {
    //----WRITE YOUR CODE BELOW THIS LINE----
    
     
    //----WRITE YOUR CODE ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    return result;
}
```

### Facilitator Solution:

```cpp
    for (size_t i=0; i< vec.size(); ++i)
       for (size_t j=i+1; j< vec.size(); ++j) 
            result = result + vec.at(i) * vec.at(j);
```

- Avoid iterating over the same vector element with `j=i+1` 

# Section Challenge:

```cpp
// Section 9
#include <iostream>
#include <vector>

using namespace std;

int main() {
    char opt{};
    vector<int> vec{};
    int num_to_add{};
    int num_average{};
    int num_smallest{};
    int num_largest{};

    do {
        cout << "-------------------------------" << endl;
        cout << "P - Print numbers" << endl;
        cout << "A - Add a number" << endl;
        cout << "M - Display mean of the numbers" << endl;
        cout << "S - Display the smallest number" << endl;
        cout << "L - Display the largest number" << endl;
        cout << "Q - Quit" << endl;
        cout << "-------------------------------" << endl;

        cin >> opt;

        switch (opt) {
            case 'p':
            case 'P': {
                cout << "-------------------------------" << endl;
                if (vec.empty()) {
                    cout << "No numbers to display." << endl;
                } else {
                    for (auto i : vec) cout << " " << i << " ";
                }
                cout << endl;
                break;
            }
            case 'a':
            case 'A': {
                do {
                    cout << "What number would you like to add?: " 
	                     << endl;
                    cin >> num_to_add;
                    vec.push_back(num_to_add);
                    cout << "Would you like to add another number? (Y/N)"
                         << endl;
                    cin >> opt;
                } while (opt != 'n' && opt != 'N');
                break;
            }
            case 'm':
            case 'M': {
                if (vec.empty()) {
                    cout << "No numbers to median." << endl;
                } else {
                    for (auto i : vec) {
                        num_average += i;
                    }
                    num_average = num_average / vec.size();
                    cout << "The average is: " << num_average << endl;
                }
                break;
            }
            case 's':
            case 'S': {
                if (vec.empty()) {
                    cout << "No numbers to display smallest." << endl;

                } else {
                    num_smallest = vec[0];
                    for (auto i : vec) {
                        if (num_smallest > i) num_smallest = i;
                    }
                    cout << "The smallest number is: " << num_smallest 
	                     << endl;
                }
                break;
            }
            case 'l':
            case 'L': {
                if (vec.empty()) {
                    cout << "No numbers to display largest." << endl;
                } else {
                    num_largest = vec[0];
                    for (auto i : vec) {
                        if (num_largest < i) num_largest = i;
                    }
                    cout << "The largest number is: " << num_largest 
		                 << endl;
                }
                break;
            }
            case 'q':
            case 'Q':
                cout << "Goodbye" << endl;
                break;
            default:
                cout << "Unkown selection, please try again";
        }
    } while (opt != 'Q' && opt != 'q');
}
```

### Areas for Improvement:

- Define the vector with a useful name like "Numbers"
- Could format the list better by enclosing them inside [] brackets.
- Could calculate the mean during the `cout` instead of assigning it first. 
- Could use `static_cast<double>()` to cast `num_average` to a double for accurate division results.
- Access the array elements using `.at()` as this will throw an `std::out_of_range` exception if you access an array element that does not exist instead of crashing.
- use `tolower()` to force the input to lowercase removing the need for checking both cases.

### Improved Code:

```cpp
// Section 9
#include <iostream>
#include <vector>

using namespace std;

int main() {
    char opt{};
    vector<int> numbers{};
    int num_to_add{};
    int total{};
    int smallest{};
    int largest{};

    do {
        cout << "-------------------------------" << endl;
        cout << "P - Print numbers" << endl;
        cout << "A - Add a number" << endl;
        cout << "M - Display mean of the numbers" << endl;
        cout << "S - Display the smallest number" << endl;
        cout << "L - Display the largest number" << endl;
        cout << "Q - Quit" << endl;
        cout << "-------------------------------" << endl;

        cin >> opt;

        switch (tolower(opt)) {
            case 'p': {
                cout << "-------------------------------" << endl;
                cout << "[ ";
                if (numbers.empty()) {
                    cout << "[] - No numbers to display." << endl;
                } else {
                    for (auto i : numbers) cout << i << " ";
                }
                cout << "]" << endl;
                break;
            }
            case 'a': {
                do {
                    cout << "What number would you like to add?: " << endl;
                    cin >> num_to_add;
                    numbers.push_back(num_to_add);
                    cout << "Would you like to add another number? (Y/N)"
                         << endl;
                    cin >> opt;
                } while (opt != 'n' && opt != 'N');
                break;
            }
            case 'm': {
                if (numbers.empty()) {
                    cout << "No numbers to median." << endl;
                } else {
                    for (auto i : numbers) total += i;
                    cout << "The average is: "
                         << static_cast<double>(total) / numbers.size() 
                         << endl;
                }
                break;
            }
            case 's': {
                if (numbers.empty()) {
                    cout << "No numbers to display smallest." << endl;
                } else {
                    smallest = numbers.at(0);
                    for (auto i : numbers) {
                        if (smallest > i) smallest = i;
                    }
                    cout << "The smallest number is: " << smallest << endl;
                }
                break;
            }
            case 'l': {
                if (numbers.empty()) {
                    cout << "No numbers to display largest." << endl;
                } else {
                    largest = numbers.at(0);
                    for (auto i : numbers) {
                        if (largest < i) largest = i;
                    }
                    cout << "The largest number is: " << largest << endl;
                }
                break;
            }
            case 'q':
                cout << "Goodbye" << endl;
                break;
            default:
                cout << "Unknown selection, please try again";
        }
    } while (opt != 'Q' && opt != 'q');
}
```
