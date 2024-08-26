# Introduction

- Function Calls have a certain amount of overhead.

- You saw what happens on the call stack.

- Sometimes we have simple functions.

- We can suggest to the compiler to compile them 'inline'
	- avoid function call overhead.
	- generate inline assembly code.
	- faster.
	- could cause code bloat.

- Compilers optimizations are very sophisticated.
	- Will likely inline even without your suggestion.

# Example: Inline Function

```cpp
inline int add_numbers(int a, int b) { // definition
	return a + b;
}

int main (){
	int result{0};
	result = add_numbers(100,200); // call
	return 0;
}
```

Here you can see the syntax for an inline function, we simply precede the function return type with the keyword `inline`.  Inline functions are usually declared in `header` or `.h` files since the definition must be available to every source file that uses it. As mentioned earlier compilers are so good now that most will make short functions like this example inline anyway even if you don't provide the `inline` keyword. 

Don't worry too much about asking the compiler to `inline` your functions but know you know what inline functions are in case you see them in other C++ code out there.