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

 