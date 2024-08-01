## The == and != operators:

- Compares the values of two expressions.
- Evaluates to a boolean (True or False, 1 or 0).
- Commonly used in control flow statements.

```
expr1 == expr2 // evaluates to true if they are equal and false if they are not

expr1 != expr2 // evaluates to false if they are equal and true if they are not

100 == 200 // will always evaluate to false

num1 != num2 // evaluates to false if they are equal and true if they are not
```

### Note: 

- The "!" exclamation symbol can also be referred to as the "bang" symbol.
- Not to be confused with a single "=" equals sign. This is an assignment operator not comparison.

### Example:

```cpp
bool result{false};

result  = (100 == 50+50); // true

result = (num1 != num2); // result = true if not equal, false if equal

cout << (num1 == num2) << endl; // 0 or 1
cout << std::boolalpha;
cout << (num1 == num2) << endl; // true or false
cout << std::noboolalpha;
```

### Example 2: Integers

```cpp
# include <iostream>

using namespace std;

int main(){
	bool equal_result{false};             // assignment
	bool not_equal_result{false};         // assignment
	
	int num1{},num2{};
	
	cout << boolalpha;
	
	cout << "Enter two integers seperated by a space: ";
	cin >> num1 >> num2;
	equal_result = (num1 == num2);
	not_equal_result = (num1 != num2);
	cout << "Comparison result (equals): " << equal_result << endl;
	cout << "Comparison result (not_equals): " << not_equal_result << endl;
}
```

### Input:

```
10 10
```

### Output:

```
Enter two integers seperated by a space: 10 10
Comparison result (equals): true
Comparison result (not_equals): false
```

### Example 3: Characters

```cpp
cout << "Enter two characters seperated by a space: ";
char char1{}, char2{};
cin >> char1 >> char2;
equal_result = (char1 == char2);
not_equal_result = (char1 != char2);
cout << "Comparison result (equals): " << equal_result << endl;
cout << "Comparison result (not_equals): " << not_equal_result << endl;
```

### Output:

```
Enter two characters seperated by a space: a b
Comparison result (equals): false
Comparison result (not_equals): true
```

### Example 4: Doubles

```cpp
cout << "Enter two doubles seperated by a space: ";
double double1{}, double2{};
cin >> double1 >> double2;
equal_result = (double1 == double2);
not_equal_result = (double1 != double2);
cout << "Comparison result (equals): " << equal_result << endl;
cout << "Comparison result (not_equals): " << not_equal_result << endl;
```

### Output:

```
Enter two doubles seperated by a space: 12.1 12.2
Comparison result (equals): false
Comparison result (not_equals): true
```

### Output: Floating fluff

```
Enter two doubles seperated by a space: 12.0 11.99999999999999999999
Comparison result (equals): true
Comparison result (not_equals): false
```

Floating point numbers are approximations and therefore 11.99999999999 will be seen as equal to 12 in this instance.

### Example 5: Mixed Mode Comparison

```cpp
cout << "Enter an integer and a double seperated by a space: ";
double double1{};
int num1{};
cin >> num1 >> double1;
equal_result = (num1 == double1);
not_equal_result = (num1 != double1);
cout << "Comparison result (equals): " << equal_result << endl;
cout << "Comparison result (not_equals): " << not_equal_result << endl;
```

The compiler will not attempt to compare an integer to a double and will instead promote the integer to a double.

### Output:

```
Enter an integer and a double seperated by a space: 10 10.0
// 10 will be promoted to 10.0
Comparison result (equals): true
Comparison result (not_equals): false
```
