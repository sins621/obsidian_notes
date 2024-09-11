# Introduction

```cpp
variable_type *pointer_name
```

```cpp
int *int_ptr;
double* double_ptr;
char *char_ptr;
string *string_ptr;
```

You should now feel very comfortable declaring variables, we've been doing it throughout the course. Well we declare pointer variables in exactly the same way except that we add the asterisk (`*`) prior to the variable name. In this context the asterisk does not function as a mathematical operator, it serves to declare the pointer.

The way you read these declarations is right to left,  so in the first example `int_ptr` is a pointer to an integer, `double_ptr` is a pointer to a double. Notice that in this declaration the asterisk is placed right next to the type, both styles are equivalent and the compiler doesn't care but there's been a long standing argument among C++ programmers concerning which is better.

`char_ptr` is a pointer to a character and `string_ptr` is a pointer to a C++ string object, just like all variables if we don't initialize our variables they will contain garbage data. In this case, all the pointer variables declared contain garbage data, so let's see how we can initialize pointer variables.

# Initializing Pointer Variables to 'Point Nowhere'

```cpp
variable_type *pointer_name {nullptr};
```

```cpp
int *int_ptr{};
double *double_ptr{nullptr};
char *char_ptr{nullptr};
string *string_ptr{nullptr};
```

In C++ it's very important that you always initialize all pointer variables before you use them, if you don't initialize a pointer variable, it will have garbage data. In this case that garbage data represents an address since that's what a pointer contains, so you can think of an uninitialized pointer as pointing anywhere. So if we use it we could be accessing memory that we have no business messing around with.

Initializing pointer variables is just like initializing non-pointer variables, we can use the initializer list syntax(`{}`). In these examples we're initializing the pointer variables to zero, that's what `nullptr` represents. This means that we're initializing the pointers to point nowhere. 

We can also initialize pointers to actually point to a variable and we'll do that in the next video. Let's review what we just talked about since it's very very important to understand.

# Summary

- Always initialize Pointers
- Uninitialized Pointers Contain Garbage Data and Can 'Point Anywhere'.
- Initializing to Zero or `nullptr` (C++ 11) represents address zero.
	- implies that the pointer is 'pointing nowhere'
- If You Don't Initialize a Pointer to Point to a Variable or Function Then You Should Initialize it to `nullptr` to 'make it null'

\