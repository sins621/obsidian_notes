std::string is a Class in the Standard Template Library

- `#include <string>` 
- std namespace
- contiguous in memory
- dynamic size
- work with input and output streams
- lots of useful member functions
- our familiar operators can be used (+,=,<,<=,>,>=,+=,= =, !=,[])
- can be easily converted to C-Style Strings if needed.
- safer (bounds checking)

# Declaring and Initializing

```cpp
#include <string>
using namespace std;

string s1;                 // Empty
string s2 {"Frank"};      // Frank
string s3 {s2};            // Frank
string s4 {"Frank", 3};    // Fra
string s5 {s3, 0, 2};      // Fr
string s6 (3, 'X');        // XXX
```

Unlike C-Style Strings, C++ Strings are always initialized. Don't have to worry about dealing with garbage in memory. 

In the case of `s2` Frank is a C-Style literal that will be converted to a C++ String. 

In the example of `s3`, `s2` is copied into this string, in other words a copy of `s2` is made and stored in `s3`.  

In the fourth example `s4` is declaring and initializing "Frank" but only the first 3 characters are being stored. 

 In the case of `s5`: `s3` is being stored into `s5`. Following the mention of `s3` you find `, 0, 2}`. The first number refers to the index in the string while the second number `2` refers to the length as a result the first two letters from `s3` are stored starting from the first (index 0).

We can also initialize a string to a specific number of a specific character. In the case of `s6`, it is initialized to 3 X's however the constructor syntax must be used ().

# Assignment `=` 

```cpp
string s1;
s1 = "C++ Rocks!";

string s2 {"Hello"};
s2 = s1;
```

# Concatenation

```cpp
string part1 {"C++"};
string part2 {"is a powerful"};

string sentence;

sentence = part1 + " " + part2 + " language";

// C++ is a powerful language

sentence = "C++" + " is a powerful"; // Illegal
```

The second example won't compile because it contains only C-Style strings however if like the first example, C++ Strings are used in conjunction with C-Style strings then it is okay. The reason for this is that the C-Style string is converted to a C++ Style string.


# Accessing Characters [] and at() method

```cpp
string s1;
string s2 {"Frank"};

cout << s2[0] << endl;
cout << s2.at(0) << endl;

s2[0] = 'f';    // frank
s2.at(0) = 'p'; // prank
```

We can use the same operators to access string elements as we do with vectors. remember that the `at()` function will perform bounds checking.

# Accessing characters [] and at() method.

For Loop with `char` type:
```cpp
string s1 {"Frank"};

for (char c: s1)
	cout << c << endl;

// Output
// F
// r
// a
// n
// k
```

For Loop with `int` type:
```cpp
string s1 {"Frank"};

for (int c: s1)
	cout << c << endl;

// Output
// 70   // F
// 114  // r
// 97   // a
// 110  // n
// 107  // k
```

In this example the ASCII values for each character are displayed.

# Comparing

```
== != > >= < <=
```

The objects are compared character by character lexically.

Can compare:
	two `std::string` objects
	 `std::string` object and C-style string literal
	 `std::string` object and C-style string variable

```cpp
string s1 {"Apple"};
string s2 {"Banana"};
string s3 {"Kiwi"};
string s4 {"apple"};
string s5 {s1};                // Apple

s1 == s5                       // True
s1 == s2                       // False
s1 != s2                       // True
s1 < s2                        // True
s2 > s1                        // True
s4 < s5                        // False
s1 == "Apple";                 // True
```

# Substrings - `substr()`

Extracts a substring from a `std::string`

	 object.substr(start_index, length)

```cpp
string s1 {"This is a test"};

cout << s1.substr(0,4);   // This
cout << s1.substr(5,2);   // is
cout << s1.substr(10,4);  // test
```

# Searching - `find()`

Returns the index of a substring in a `std::string`

	 object.find(search_string)

```cpp
string s1 {"This is a test"};
							// Output
cout << s1.find("This");    // 0
cout << s1.find("is");      // 2
cout << s1.find("test");    // 10
cout << s1.find('e');       // 11
cout << s1.find ("is", 4);  // 5
cout << s1.find("XX");      // string::npos
```

The `find` method works with characters and strings.

The difference between `s1.find("is")` and `s1.find("is", 4);` is that the second command will start from index 4 and that's why the result is different. The first command finds the "is" in "This" whereas the second command finds the "is" after "This".

In the final example the method returns `string::npos` because there is no position where "XX" is found.

Side note: The `rfind()` method starts from the back of the string.

# Removing characters - `erase()` and `clear()`

Removes a substring of characters from a `std::string`

	 object.erase(start_index, length)

```cpp
string s1 {"This is a test"};

cout << s1.erase(0,5);     // is a test
cout << s1.erase(5,4);     // is a
s1.clear();                // empties string s1
``` 

# Other useful methods

```cpp
string s1{"Frank"};

cout << s1.length() << endl;       // 5

s1 += " James";
cout << s1 << endl;                // Frank James
```

Many more...

# Input `>>` and `getline()`

Reading `std::string` from `cin`

```cpp
string s1;
cin >> s1;          // "Hello there" entered.

cout << s1 << endl;

// Output
// Hello            This is because the information is only accepted                          until the first space.

getline(cin,s1);    // read entire line until \n
cout << s1 << endl;

// Output
// Helo there

getline(cin, s1, 'x');  // this isx
						// x in this case is the delimiter, meaning                                  input will be accepted until 'x'.
cout << s1 << endl;       // this is
```

