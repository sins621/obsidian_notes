# C++ Programs

- C++ Standard Libraries (functions and classes)
- Third-party Libraries (functions and classes)
- Our own functions and classes

# Functions allow the modularization of a program

- Separate code into logical self-contained units
- These units can be reused

# Modularized Code:

How we have been writing code:
```cpp
int main() {
// Read Input
	statement1;
	statement2;
	statement3;
	statement4;

// Process Input
	statement5;
	statement6;
	statement7;

// Provide Output
	statement8;
	statement9;
	statement10;

	return 0;
}
```

Modularized Code:
```cpp
int main() {
// Read Input
	read_input();

// Process Input
	process_input();

// Provide Output
	provide_output();
}
```

 In the first example you can see how we have been writing code up to this point. Lot's of statements after one another, some of these statements might be if statements, some might be looping statements but you can see that this program has 3 logical sections. One for input, one for processing and one for output but everything is placed int the `main` function. This is okay for relatively small programs like the ones we have written.   