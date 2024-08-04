# Coding Examples:

```cpp
string s0;
string s1{"Apple"};
string s2{"Banana"};
string s3{"Kiwi"};
string s4{"apple"};
string s5{s1};       // Apple
string s6{s1, 0, 3}; // App
string s7(10, 'x');  // XXXXXXXXXX

cout << s0 << endl;          // No Garbage
cout << s0.length() << endl; // Empty String
```

`string s0;`

This has been initialized to nothing but thankfully when we run the line `cout << s0 << endl;` there will be nothing in the output because it will not allow garbage memory to be printed here. 

The line `cout << s0.length() << endl;` will return 0 because `s0` has no length.

```cpp
string s1{"Apple"};
string s2{"Banana"};
string s3{"Kiwi"};
string s4{"apple"};
```

Regular Assignment.

`string s5{s1};` 

`s5` Has been initialized to the value of `s1` and now contains "Apple".

`string s6 {s1, 0, 3};`

`s6` has been initialized to the value of `s1` however do to the argument following `s1`: `, 0, 3}` it has been assigned the first 3 letters which are "App" this is because it has been assigned 3 letters of `s1` starting from index 0, or the beginning of the string.

`string s7 (10, 'X');`

`s7` Has been assigned 10 Xs: "XXXXXXXXXX". Note: Regular Parenthesis have to be used here ().

## Initialization

```cpp
cout << "\nInitialization"
     << "\n________________________" << endl;
cout << "s1 is initialized to: " << s1 << endl;
cout << "s2 is initialized to: " << s2 << endl;
cout << "s3 is initialized to: " << s3 << endl;
cout << "s4 is initialized to: " << s4 << endl;
cout << "s5 is initialized to: " << s5 << endl;
cout << "s6 is initialized to: " << s6 << endl;
cout << "s7 is initialized to: " << s7 << endl;

// Output

/*Initialization
________________________
s1 is initialized to: Apple
s2 is initialized to: Banana
s3 is initialized to: Kiwi
s4 is initialized to: apple
s5 is initialized to: Apple
s6 is initialized to: App
s7 is initialized to: XXXXXXXXXX */
```

## Comparison

```cpp
cout << "\nComparison"
<< "\n------------------------------" << endl;
cout << boolalpha;
cout << s1 << " == " << s5 << ": " 
     << (s1 == s5) << endl; // True Apple == Apple
cout << s1 << " == " << s2 << ": " 
     << (s1 == s2) << endl; // False Apple != Banana
cout << s1 << " != " << s2 << ": " 
     << (s1 != s2) << endl; // True Apple != Bananan
cout << s1 << " < " << s2 << ": " 
     << (s1 < s2) << endl;   // True Apple < Banana
cout << s2 << " > " << s1 << ": " 
     << (s2 > s1) << endl;   // True Banan > Apple
cout << s4 << " < " << s5 << ": " 
     << (s4 < s5) << endl;   // False apple > Apple
cout << s1 << " == " << "Apple" << ": " 
     << (s1 == "Apple") << endl; // True Apple = Apple

/* Output
Comparison
------------------------------
Apple == Apple: true
Apple == Banana: false
Apple != Banana: true
Apple < Banana: true
Banana > Apple: true
apple < Apple: false
Apple == Apple: true */
```

## Assignment

```cpp
cout << "\nAssignment" << "\n__________________" << endl;

s1 = "Watermelon";
cout << "s1 is now: " << s1 << endl;
s2 = s1;
cout << "s2 is now: " << s2 << endl;

s3 = "Frank";
cout << "s3 is now: " << s3 << endl;

s3[0] = 'C';
cout << "s3 changed first letter to C: " << s3 << endl;
s3.at(0) = 'P';
cout << "s3 changed first letter to P: " << s3 << endl;

/*Assignment
__________________
s1 is now: Watermelon
s2 is now: Watermelon
s3 is now: Frank
s3 changed first letter to C: Crank
s3 changed first letter to P: Prank*/
```

 ## Concatenation

```cpp
s3 = "Watermelon";
cout << "\nConcatenation " << "\n______________" << endl;

s3 = s5 + " and" + s2 + " juice"; // Apple and Banana Juice
cout << "s3 is now: " << s3 << endl; // Apple and Banana Juice

// s3 = "nice " + " cold " + s5 + "juice"; // Comipler Error

/* Output:
Concatenation 
______________
s3 is now: Apple andBanana juice*/
```

## `for` loop

```cpp
cout << "\nLooping" << "\n-------------------------" << endl;

s1 = "Apple";
for (size_t i {0}; i < s1.length(); ++i)
	cout << s1.at(i);
cout << endl;

/* Ouptut
Looping
-------------------------
Apple*/
```

 ## Range-based `for` loop

```cpp
cout << "\nLooping" << "\n-------------------------" << endl;

s1 = "Apple";
for (char c:s1)
	cout << c;
cout << endl;

/* Ouptut
Looping
-------------------------
Apple*/
```

## Substring

```cpp
cout << "\nSubstring" << "\n--------------------------" << endl;
s1 = "This is a test";

cout << s1.substr(0,4) << endl;    // This
cout << s1.substr(5,2) << endl;    // is
cout << s1.substr(10,4) << endl;   // test

/*Output
cout << "\nSubstring" << "\n--------------------------" << endl;
s1 = "This is a test";

cout << s1.substr(0,4) << endl;    // This
cout << s1.substr(5,2) << endl;    // is
cout << s1.substr(10,4) << endl;   // test*/
```

## Erase

```cpp
cout << "\nErase" << "\n---------------------------" << endl;

s1 = "This is a test";
s1.erase(0,5);          //Erase This from s1 results in "is a test"
cout << "s1 is now: " << s1 << endl;  // is a test

/*Output
Erase
---------------------------
s1 is now: is a test*/
```

## Getline

```cpp
cout << "\ngetline" << "\n-------------------" << endl;

string full_name {};

cout << "Enter your full name ";
getline(cin, full_name);

cout << "Your full name is: " << full_name << endl;

/*Output
getline
-------------------
Enter your full name Bradly Carpenter
Your full name is: Bradly Carpenter*/
```

## Find

```cpp
cout << "\nfind" << "\n------------------------" << endl;

s1 = "The secret word is Boo";
string word{};

cout << "Enter the word to find: ";
cin >> word;

size_t position = s1.find(word);
if (position != string::npos)
	cout << "Found " << word << " at position: " << position << endl;
else
	cout << "Sorry, " << word << " not found" << endl;

cout << endl;

/*Output
find
------------------------
Enter the word to find: Boo
Found Boo at position: 19*/
```

# Section Challenge: 

## Using C++ Strings - Exercise 1

In this exercise you will create a program that will be used to reformat a name so that it can be read more easily.

The string variable `unformatted_full_name` is comprised of two substrings; `first_name` and `last_name` in that order. Each substring begins with a capital letter.

Begin by declaring and initializing the string variable `first_name` from the string variable `unformatted_full_name` remembering that when initializing from another string, the first integer within the curly brackets represents the starting index of the substring you wish to copy and the second integer represents the length of the substring.

Next, declare and initialize the string variable `last_name` by using the assignment operator `=` and the string function `substr` on the string variable `unformatted_full_name`.

Next, declare and initialize the string variable `formatted_full_name`. This should be done through the use of the concatenation operator `+` by concatenating the string variables `first_name` and `last_name` in that order, and then assigning the concatenated string to `formatted_full_name` using the assignment operator `=`.

Now the string variable `formatted_full_name` contains the string `"StephenHawking"`. We see that the string is no more formatted than the original string variable `unformatted_full_name` and that is because the addition operator `+` does not add whitespace between strings when concatenating them.

Fortunately, we can use the string function `insert` on the string variable `formatted_full_name` to insert a whitespace between the substrings such that `formatted_full_name` will then contain the string `"Stephen Hawking"`.

```cpp
#include <iostream>
#include <string>
using namespace std;

void cpp_strings() {
    
    string unformatted_full_name {"StephenHawking"};
    
    //----DO NOT MODIFY THE CODE ABOVE THIS LINE----
    //----WRITE YOUR CODE BELOW THIS LINE----
    
    
    
    //----WRITE YOUR CODE ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    
    cout << formatted_full_name;
}
```