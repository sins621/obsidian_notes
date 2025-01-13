# The Address Operator `&`

- Variables Are Stored in Unique Addresses

- Unary Operator

- Evaluates to the Address of it's Operand

	- Operand Cannot be a Constant or Expression That Evaluates to Temp Values

In this lesson we'll learn how to access the address or location in memory of any variable, we'll also learn how to initialize a [pointer](https://www.youtube.com/watch?v=2ybLD6_2gKM&t=438s) variable to point to another variable.

In C++ we can use the address operator which is the ampersand symbol `&` to the left side of an operand. The address operator is a unary operator and when used in an expression it evaluates to the address of it's operand.

Of course the operand must have an [L Value](../../Generic%20Concepts/L%20Value.md), so it can't be a constant or an expression that evaluates to temporary values. 

```cpp
int num{10};

cout << "Value of num is " << num << endl;          // 10
cout << "sizeof num is: " << sizeof num << endl;    // 4
cout << "Address of num is: " << &num << endl;      // 0x61ff1c
```

In the example code we have a variable num which is a simple integer variable that's been initialized to 10, if we display `num` then we are displaying the contents of num which is 10. 

If we display the size of `num` then we're displaying how much storage is allocated by `num`, in other words how much storage do we need on my machine to store an integer. In this case it's 4 bytes.  

Finally, if we display the address of num using the address operator we get a hexadecimal number that represents the location in memory of the variable `num`. A hexadecimal number is just a base 16 number.

So far so good, you can see that the address operator evaluates exactly what we expect, the address of the variable num. Now let's see these same statements with pointer variables.

# The Address Operator - Example

```cpp
int *p;

cout <<  "Value of p is: " << p << endl;             // 0x61ff60 - garbage

cout << "Address of p is: " &p << endl;              // 0x61ff18

cout << "sizeof of p is: " << sizeof p << endl;      // 4

p = nullptr;         // set p to point nowhere

cout << "Value of p is: " << p << endl;              // 0
```

In the first line we declare `p` to be a pointer to an integer variable so that means that p can hold values that are addresses of integers, also notice that we didn't initialize the pointer `p`.

In the first output statement we're displaying the value of `p`. The value of p is the value that's stored in `p`. Since we didn't initialize `p` we have garbage data in `p` and you can see that address displayed.

In the second output statement we're displaying the address of the variable `p`, since we're using the address operator.

In the third statement we display the size of `p` using the `sizeof` operator. 

In the next line we assign `nullptr` to `p`, this sets `p` to zero which means it's pointing nowhere. Since `p` is a variable we can change it's value, this seems obvious but it's important since when we talk about references in a bit you'll see that you can't change a reference once it's initialized. 

Finally, in the last output statement we display the value of `p` again and this time zero is returned because we zeroed it out. Even though these examples seem pretty simple but it's important to test them on your own machine and make sure that you understand these concepts. 

# `sizeof` a Pointer Variable

- Don't confuse the size of a pointer and the size of what it points to.
- All pointers in a program have the same size.
- They may be pointing to very large or very small types.

Here you can see that we're defining 5 pointer variables `p1` through `p5` and initializing them all to `nullptr`. Each pointer variable points to a different type, so each can hold addresses of variables of the type they point to.

```cpp
int *p1 {nullptr};
double *p2{nullptr};
unsigned long long *p3{nullptr};
vector<string> *p4 {nullptr};
string *p5 {nullptr};
```

If we displayed the size of each of these pointer variables what do you think might be displayed? Would the size of `p1` be less than the size of `p4` because `p1` points to an int and `p4` to a vector object? If you said `p4` was larger, you'd be wrong. Based on the previous example, all pointers in our program will hold values that can be represented in 8 bytes. An address of an integer and an address of a string all have a size of 8 bytes on our machines. 

There is a big difference between the size of the pointer variable itself and the size of what it points to. Again, take your time and make sure you understand the difference between a pointer and what it points to. 

# Typed Pointers

The compiler will make sure that the address stored in a pointer variable is of the correct type.

```cpp nums
int score {10};
double high_temp{100.7};

int *score_ptr{nullptr};

score_ptr = &score;                      // OK
score_ptr = &high_temp;                  // Compiler Error
```

We've declared pointers so far as **typed pointers**, this means that we explicitly declare the pointer variable to point to a variable of a specific type. In this example we're declaring an integer `score` and initializing it to 10, and a double `high_temp` and initializing it too 100.7. Then we declare `score_ptr` as a pointer to an integer, now we assign the address of `score` to `score_ptr`, the compiler is happy with that, since `score_ptr` holds addresses of integers and `score` is an integer.

However in the last assignment statement we're assigning the address of `high_temp` to `score_ptr`, the compiler won't let us do this, we'll be presented with a compiler error. We told the compiler at line 4 that `score_ptr` holds addresses of integers, but we're asking it store the address of a double. Both addresses are 4(8) bytes long so the issue isn't that the size won't fit but rather that there is a **type conflict**.

In C++ we can also have untyped void pointers, they're out of the scope for this lesson but they aren't used that much in C++, they're more often used in C.

# Storing an Address in Pointer Variables

- Pointers Are Variables so They Can Change.
- Pointers Can be Null.
- Pointers Can be Uninitialized.

Let's review a very simple concept but a very important concept, pointers are variables so they can change. Pointers can be `null` and pointers can be uninitialized, that's not usually a good idea but it can happen.

The example code shows all these options, first we declare two double variables; high and low temp and we initialize them. Then we declare `temp_ptr` as a pointer to a double and we don't initialize it so it's pointing anywhere. Then we assign the address of `high_temp` to `temp_ptr`, and then we change `temp_ptr` to point somewhere else by assigning it to the address of `low_temp`. Finally we null out `temp_ptr` by assigning it to `nullptr`.

```cpp nums
double high_temp{100.7};
double low_temp{37.2};

double *temp_ptr;

temp_ptr = &high_temp;         // points to high_temp
temp_ptr = &low_temp;         // points to low_temp

temp_ptr = nullptr;
```

# Examples in the IDE:

```cpp nums
int num{10};
cout << "Value of num is: " << num << endl;
cout << "sizeof num is: " << sizeof num << endl;
cout << "Address of num is: " << &num << endl;

int *p;
cout << "\nValue of p is: " << p << endl;        // Garbage or not????
cout << "sizeof p is: " << sizeof p << endl;
cout << "Address of p is: " << &p << endl;

p = nullptr;
cout << "Value of p is: " << p << endl;        // Null

int *p1 {nullptr};
double *p2{nullptr};
unsigned long long *p3{nullptr};
vector<string> *p4 {nullptr};
string *p5 {nullptr};

cout << "\nsizeof p1 is: " << sizeof p1 << endl;
cout << "sizeof p2 is: " << sizeof p2 << endl;
cout << "sizeof p3 is: " << sizeof p3 << endl;
cout << "sizeof p4 is: " << sizeof p4 << endl;
cout << "sizeof p5 is: " << sizeof p5 << endl;

int score{10};
double high_temp{100.7};

int *score_ptr{nullptr};

score_ptr = &score;
cout << "\nValue of score is: " << score << endl;
cout << "Address of score is: " << &score << endl;
cout << "Value of score_ptr is: " << score_ptr << endl;

// score_ptr = &high_temp; // Compiler Error
```

## Output:

```
Value of num is: 10
sizeof num is: 4
Address of num is: 0x3d35dffe64

Value of p is: 0x7ff702911850
sizeof p is: 8
Address of p is: 0x3d35dffe58
Value of p is: 0

sizeof p1 is: 8
sizeof p2 is: 8
sizeof p3 is: 8
sizeof p4 is: 8
sizeof p5 is: 8

Value of score is: 10
Address of score is: 0x3d35dffe54
Value of score_ptr is: 0x3d35dffe54
```