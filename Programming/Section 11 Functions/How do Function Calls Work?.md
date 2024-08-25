# Introduction:

- Functions use the 'Function Call Stack'
	- Analogous to a Stack of Books
	- LIFO - Last In First Out
	- Push and Pop

- Stack Frame or Activation Record
	- Functions Must Return Control to the Function that Called It
	- Each Time a Function is Called we Create a New Activation Record and Push It on the Stack
	- When a Function Terminates we Pop the Activation Record and Return.
	- Local Variables and Function Parameters are allocated on the Stack.

- Stack Size is Finite - Stack Overflow

# The Stack:

![](Pictures/The%20Stack.png)

# Example: Two Function Stack with Reference

```cpp
#include <iostream>

using namespace std;

void func2(int &x, int y, int z){
    x+= y + z;
}

int func1(int a, int b){
    int result{};
    result = a + b;
    func2(result,a,b);
	return result;
}

int main(){
    int x{10};
    int y{20};
    int z{};
    z = func1(x,y);
    cout << z << endl;    
}
``` 

Note that in this example `result` is being updated via `func2()` because there is a reference being made to the variable with the `&` symbol thus changing it's value directly in the function. 

What typically happens when main calls `func1()` (or any function calls another)?
There are other ways to achieve the same results :)

`main()`:
	 push space for the return value
	 push space for the parameters
	 push the return address
	 transfer control to `func1()` (jmp)
`func1()`:
	 push the address of the previous activation record
	 push any register values that will need to be restored before returning to the caller
	 perform the code in `func1()`
	 restore the register values
	 restore the previous activation record (move the stack pointer)
	 store any function result
	 transfer control to the return address (jmp)
`main()`
	 pop the parameters
	 pop the return value

## Steps:

Let's visualize how the values are changed on the stack.

### `main()` -> `func1()`:

![](Pictures/Stack%20main%20to%20func1.png)

### `func1()` to `func2()`:

![](Pictures/func1%20to%20func2%20one.png)

- Copies of the values of `x` and `y` are made into `a` and `b`.

![](Pictures/func1%20to%20func2%20part%202.png)

### `func2()`

![](Pictures/func2%20part%201.png)

- `y` and `z` are copied from `a` and `b` however `x` is assigned to the memory location of `result` and is equal to it's exact value. `x` is an *alias* for `result`.
- 
![](Pictures/func2%20part%202.png)

### `func2()` back to `func1()`

![](Pictures/func2%20to%20func1.png)

- `func2()` comes off the stack and we pickup where we left off returning `result` which is now 60.
### back to `main()`

![](Pictures/back%20to%20main.png)
