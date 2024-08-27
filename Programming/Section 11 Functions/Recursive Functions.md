# Introduction

- A recursive function is a function that calls itself.
	- Either directly or indirectly through function

- Recursive Problem Solving
	- Base Case
	- Divide the rest of Problem into Subproblem and do Recursive Solutions

- There are Many Problems that Lend Themselves to Recursive Solutions.

- Mathematical - Factorial, Fibonacci, Fractals, etc.

 - Searching and Sorting - Binary Search, Search Trees, etc.

 # Example - Factorials

Here's a quick catch-up lesson on [[Factorials]].

```cpp
0! = 1
n! = n * (n-1)!
```

- Base Case:
	- factorial(0) = 1

- Recursive Case:
	- factorial(n) = n * factorial(n-1)

