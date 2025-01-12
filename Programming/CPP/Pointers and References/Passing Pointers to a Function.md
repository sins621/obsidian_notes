# `const` and Pointers

- There are several ways to qualify pointers using `const`

	- Pointers to Constants
	
	- Constant Pointers
	
	- Constant Pointers to Constants

So far our use of `const` with function reference parameters essentially makes them read only however in C++ we can qualify we a pointer in several ways. 

Firstly, we don't need to use constants at all, in this case we have a pointer just as we've been using up to this point. We can change the data the pointer is pointing to and we can change the pointer itself and make it point somewhere else.

The `const` qualifier provides more finer grain control of what we allow to be changed, we can have pointers to constants, constant pointers and constant pointers to constants, these will be very useful when we pass pointers to functions in the next lesson. Let's take a look at each one of them:

# Pointers to Constants

- The Data Pointed to by the Pointers is Constant and Cannot be Changed.

-  The Pointer Itself can Change and Point Somewhere Else.

In the case of pointers to constants, the data pointed to by the pointer is constant and can't be changed. However, the pointer itself can change and point elsewhere.

```cpp nums
int high_score {100};
int low_score {65};
const int *score_ptr {&high_score};

*score_ptr = 86;        // ERROR
score_ptr = &low_score; // OK
```

In this example we have two integers declared and initialized, these are `high_score` and `low_score`, but this time when we declare the pointer we use the `const` qualifier before the type that we point to, so `score_ptr` is a pointer to an integer constant and we initialize it to point to `high_score`. If we attempt to change the value of the pointed to data, in this case `high_score`, we'll be presented with a compiler error. However, we're free to assign another address to the pointer and have it point somewhere else as we do on line 6. 

# Constant Pointers

- The Data Pointed to by the Pointers can be Changed.

- The Pointer Itself Cannot Change and Point Somewhere Else.

In the case of constant pointers it's the pointer itself that's constant, so the data pointed to by the pointer can be changed via the pointer however the pointer itself cannot be changed and cannot point to anything else.

```cpp nums
int high_score {100};
int low_score {65};
int const *score_ptr {&high_score};

*score_ptr = 86;        // ERROR
score_ptr = &low_score; // OK
```

Notice that we still use the `const` qualifier however we use it before the asterisk in the pointer declaration so we're declaring `score_ptr` as a constant pointer to an integer. 

# Constant Pointers to Constants

- The Data Pointed to by the Pointer is Constant and **Cannot** be Changed.

- The Pointer Itself **Cannot** Change and Point Somewhere Else.

In this case it's a constant pointer to constants, we need to use the constant qualifier twice in the pointer declaration. So the data pointed to by the pointer is constant and can't change and the pointer itself is constant and can't be changed. 

```cpp nums
int high_score {100};
int low_score {65};
const int const *score_ptr {&high_score};

*score_ptr = 86;        // ERROR
score_ptr = &low_score; // OK
```

Notice the syntax, `score_ptr` is a constant pointer to an integer constant, in this case if we try to modify either the data or the pointer we'll be presented with compiler errors. 