# The Address Operator `&`

- Variables Are Stored in Unique Addresses

- Unary Operator

- Evaluates to the Address of it's Operand

	- Operand Cannot be a Constant or Expression That Evaluates to Temp Values

```cpp
int num{10};

cout << "Value of num is " << num << endl;          // 10
cout << "sizeof num is: " << sizeof num << endl;    // 4
cout << "Address of num is: " << &num << endl;      // 0x61ff1c
```


In this lesson we'll learn how to access the address or location in memory of any variable, we'll also learn how to initialize a pointer variable to point to another variable.

In C++ we can use the address operator which is the ampersand symbol `&` to the left side of an operand. The address operator is a unary operator and when used in an expression it evaluates to the address of it's operand.