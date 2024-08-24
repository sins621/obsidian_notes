# Introduction

- C++ uses scope rules to determine where an identifier can be used.

- C++ uses static or lexical scoping

- Local or Block Scope

- Global Scope

# Local or Block Scope

- Identifiers declared in a block {}

- Function parameters have block scope.

- Only visible within the block {} where declared.

- Function Local Variables are only active while the function is executing.

- Local variables are NOT preserved between function calls.

- With nested blocks inner blocks can 'see' out but outer blocks cannot 'see' in.

# Static Local Variables

- Declared with static qualifier.

	  static int value {10};

- Value IS preserved between function calls.

- Only initialized the first time the function is called.

# Global Scope

- Identifier declared outside any function or class.

- Visible to all parts of the program after the global identifier has been declared.

- Global Constants are OK.

- Best Practice - Don't use global variables.

# In the IDE:

```cpp
#include <iostream>
using namespace std;

int num{300};

void local_example(int x){
    int num{1000}; // Local to local_example
    cout << "\nLocal num is: " << num 
	    << " in local_example - start" << endl;
    num=x;
    cout << "Local num is: " << num 
	    << " in local_example - end" << endl;
    // num1 in main is not within scope - so it can't be used here.
}

void global_example(){
    cout << "\nGlobal num is: " << num 
	    << " in global_example - start" << endl;
    num *= 2;
    cout << "Global num is: " << num 
	    << " in global_example - end" << endl;
}

void static_local_example(){
    static int num{5000}; /* local to static_local_example
    static - retains it's value between calls*/
    cout << "\nLocal static num is: " << num 
	    << " in static_local_example - start" << endl;
    num+=1000;
    cout << "Local static num is: " << num 
	    << " in static_local_example - end" << endl;
}

int main(){
    int num{100}; // Local to Main
    int num1{500}; // Local to Main

    cout << "Local num is: " << num << " in main" << endl;

    { // Creates a new level of scope
        int num{200}; // Local to this inner block << endl;
        cout << "Local num is: " << num 
	        << " in inner block in main" << endl;
        cout << "Inner block in main can see out - num 1 is: " 
	        << num1 << endl;
    }

    cout << "Local num is: " << num << " in main" << endl;

    local_example(10);
    local_example(20);

    global_example();
    global_example();
    static_local_example();
    static_local_example();
}
```

```
Output:

Local num is: 100 in main
Local num is: 200 in inner block in main
Inner block in main can see out - num 1 is: 500
Local num is: 100 in main

Local num is: 1000 in local_example - start
Local num is: 10 in local_example - end

Local num is: 1000 in local_example - start
Local num is: 20 in local_example - end

Global num is: 300 in global_example - start
Global num is: 600 in global_example - end

Global num is: 600 in global_example - start
Global num is: 1200 in global_example - end

Local static num is: 5000 in static_local_example - start
Local static num is: 6000 in static_local_example - end

Local static num is: 6000 in static_local_example - start
Local static num is: 7000 in static_local_example - end
```

