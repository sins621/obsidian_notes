# Introduction

- A recursive function is a function that calls itself.
	- Either directly or indirectly through function

- Recursive Problem Solving
	- Base Case
	- Divide the rest of Problem into Subproblem and do Recursive Solutions

- There are Many Problems that Lend Themselves to Recursive Solutions.

- Mathematical - Factorial, Fibonacci, Fractals, etc.

 - Searching and Sorting - Binary Search, Search Trees, etc.

# Example: Factorials

Here's a quick catch-up lesson on [Factorials](../../Math/Factorials.md).

```cpp
0! = 1
n! = n * (n-1)!
```

- Base Case:
	- factorial(0) = 1

- Recursive Case:
	- factorial(n) = n * factorial(n-1)

```cpp
unsigned long long factorial(unsigned long long n){
	if (n == 0){
		return 1;                // base case
	}
	return n * factorial (n-1);  // recursive case
}

int main(){
	cout << factorial(8) << endl; // 40320
	return 0;
}
```

So let's look at the code starting at `main()`, we call `factorial()` and pass in an 8 to the `factorial()` function. When the `factorial()` function returns, the value returned will be output to the console. In this case we expect 40320. 

Let's look at the factorial function. First we need to decide which types we'll except and return. The `factorial()` function can generate massively huge numbers, so in this case we're using unsigned long long as the return type and the parameter type. This can hold very very large positive integers but we can still get an overflow even with such a big number. 

If you look at the code for the factorial function it looks exactly like the mathematical definition of factorial. We check a base case, in this case if `n` is equal to zero we return 1. Remember, the `return` knocks you out of the function immediately. Otherwise we return the result of calling the `factorial()` function with `n-1`. So in this case it would be `return` `n` times call `factorial()` with `n-1`. There's the recursion, the base case is super important since it's what stops the recursion, otherwise we'd recurse indefinitely and eventually we'd run out of stack space and get a stack overflow error. 

Let's look at calculating a Fibonacci number.

# Example: Fibonacci Number

```
Fib (0) = 0
Fib (1) = 1
Fib (n) = Fib(n-1) + Fib(n-2)
```

- Base Case:
	- Fib(0) = 0
	- Fib(1) = 1

- Recursive Case:
	- Fib(n) = Fib(n-1) + Fib(n-2)

