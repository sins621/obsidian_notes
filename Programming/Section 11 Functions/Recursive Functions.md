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

```
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

Need a refresher? Read through this revision of [Fibonacci Numbers](../../Math/Fibonacci%20Numbers.md).

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

# In the IDE:

```cpp
#include <iostream>

using namespace std;

unsigned long long fibonacci (unsigned long long n){
	if (n <= 1){
		return n;        // base cases
	}
	return fibonacci(n-1) + fibonacci(n-2); // recursion
}

int main(){
	cout << fibonacci(30) << endl; // 832040
	return 0;
}
```

Again, we're using unsigned long long in this case since Fibonacci can also produce huge numbers. Notice in the `main()` function we call `fibonacci()` and the result we expect back is `832040`.

Now let's look at the `fibonacci()` function, notice that in the **base case** if `n` is less than or equal to `1` then we simply return `n`. So when `n` is `0` we return `0` and when `n` is `1` we return `1`. That handles both **base cases** in one step. We can easily rewrite this condition to explicitly check `n=0` and `n=1` but this achieves the same result. This base case is what stops the recursion, if `n` not `0` or `1` then we call `fibonacci()` again with both pieces of the problem definition. Eventually the recursion will stop and the result will be returned to `main()`. 

Notice how much the code looks exactly like the mathematical definition of Fibonacci. This is by design, let's look at a few thoughts on recursion:
# Important Notes:

- If a recursion doesn't eventually stop you will have infinite recursion.

- Recursion can be resource intensive.

- Remember the base case(s).
	- They terminate the recursion.

- Only use recursive solutions when it makes sense.

- Anything that can be done recursively can be done iteratively.
	- Stack overflow error.

# Example 1: Factorial Visualized

Building up the stack for line 5 till the base case:

![](Pictures/Recursive%20Functions%20-%20Factorial%20Visualized.png)

Once we reach that point every stack is popped off one by one returning it's value:

![](Pictures/Recursive%20Functions%20-%20First%20Stack%20Popped%20Off.png)

![](Pictures/Recursive%20Functions%20-%20Second%20Function.png)

![](Pictures/Recursive%20Functions%20-%20Final%20Stack%20Popped%20Off.png)

