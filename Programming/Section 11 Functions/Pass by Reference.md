# Introduction

- Sometimes we want to be able to change the actual parameter from within the function body.

- In order to achieve this we need the location or address of the actual parameter.

- We saw how this is the effect with array, but what about other variable types?

- We can use reference parameters to tell the compiler to pass in a reference to the actual parameter.

- The formal parameter will now be an alias for the actual parameter.

# Example: Ampersand Symbol '&'

In this example we have a function named `scale_number()` notice that the parameter given to the function is not an `int` named `num`, it's a reference to an `int` named `num`. That's what the ampersand "&" symbol does, so now when we use `num` in the function body we're referencing the actual parameter.

Let's walk through this.

```cpp
void scale_number(int $num); // prototype

int main(){
	int number {1000};
	scale_number(number);     // call
	cout << number << endl;   // 100
	return 0;
}

void scale_number(int &num){  // definition
	if (num > 100)
		num = 100;
}
```

In `main()` we declare an integer `number` an initialize it to 1000, then we call the `scale_number()` function and pass in the *actual* parameter `number`. We now transfer control to the `scale_number()` function since the *formal* parameter in the `scale_number()` function is a reference parameter, this means that `num` is an alias for `number`, if we change `num` we're changing `number`. Behind the scenes the location of `number` is being passed in to the function.

So the code in `scale_number()` checks to see if the number is greater than 100, in this case it is, it's 1000, so we set the number to 100 and the function completes. When we return to main and display `number` it will display 100. 

Pass by reference can be super useful for several reasons, first it allows us to change an *actual* parameter if we need to, secondly we don't make a copy of the parameter which could be large and take time but we have to be aware of potentially unwanted changes.

Let's see how we could swap two numbers using pass by reference.

# Example: Swap Numbers

```cpp
void swap(int &a, int &b);

int main(){
	int x{10}, y{20};
	cout << x << " " << y << endl; // 10 20
	swap (x, y);
	cout << x << " " << y << endl; // 20 10
	return 0;
}

void swap(int &a, int &b){
	int temp = a;
	a = b;
	b = temp;
}
```

In this example we're writing a function that swaps the values of the two integers passed into it. Take a look at `main()`, `x` is 10 and `y` is 20. `x` And `y` are first displayed and we get 10 and 20, just as we expect. Then we call `swap()` and pass in `x,y`, then we display `x,y` again now they're 20 and 10, we swapped them.  

Look at the function definition and notice that both `a` and `b` are reference parameters, so when we call this function with `x` and `y`, `a` and `b` become aliases to `x` and `y` respectively. In the body of the function we set `temp` to `a`, then `a` to `b` and then `b` to `temp` and we've swapped the two values that were passed into us. 

What do you think would happen if we didn't use pass by reference and we used pass by value? Well the *actuals* would be copied so we would swap the copies in the function and then return, when we get back to `main()` the actuals haven't changed since we were working with copies.

Let's talk a little bit about how parameters are passed into functions.

# Example: Vector - pass by value

```cpp
void print(std::vector<int> v);

int main(){
	std::vector<int> data{1,2,3,4,5};
	print(data);
	return 0;
}

void print(std::vector<int> v){
	for (auto num: v)
		cout << num << endl;
}
```

Let's see what happens when we pass in a vector object to a function, in this case we have a function called `print()` and it expects a vector of integers. Notice that in this case we're using pass by value. Inside the `print()` function we simply use a range based for loop and display the vector elements, pretty easy, but there's one issue with this code. 

That is, we're using pass by value. So we're making a complete copy of the vector object in the function so the *formal* parameter `v` will be a copy of the *actual* parameter `data` in this case. In order to make a copy we need to allocate storage and copy values over, if the vector is very large we could run into performance and storage issues. So, why don't we use pass by reference instead? So we can avoid the copy. 

Let's do it.
# Example: Vector - pass by reference

```cpp
void print(std::vector<int> &v);

int main(){
	std::vector<int> data {1,2,3,4,5};
	print(data);
}

void print(std::vector<int> &v){
	for (auto num: v)
		cout << num << endl;
}
```

Notice that we're using pass by reference, as we've declared the *formal* parameter `v` as a reference parameter using the ampersand. The output of this program is exactly the same as before, but we avoid the storage and copy overhead of pass by value.

But there is one issue, since we're using pass by reference, the `print()` function could change the value of the vector, it could even erase the entire vector. This is probably not a good idea, so let's tell the compiler that this is a constant reference. 
# Example: Vector - pass by `const` reference

```cpp
void print(const std::vector<int> &v);

int main(){
	std::vector<int> data {1,2,3,4,5};
	print(data);
	return 0;
}

void print(const std::vector<int> &v){
	v.at(0) = 200;                      // ERROR
	for (auto num: v)
		cout << num << endl;
}
```

So now we've added the `const` keyword to the parameter, now we've told the compiler to use pass by constant reference so if we try to make any changes to the *formal* parameter `v` in the function we'll be presented with a compiler error. 

This is really the best of both worlds since we're more efficiently passing information to the function but we're still ensuring that the function can't change the data by mistake. 

Let's head over to the IDE to see this in action.

# In the IDE:

```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

void pass_by_ref1(int & num);
void pass_by_ref2(string &s);
void pass_by_ref3(vector <string> &v);
void print_vector(const vector<string> &v); // const

void pass_by_ref1(int & num){
    num = 1000;
}

void pass_by_ref2(string &s){
    s = "Changed";
}

void pass_by_ref3(vector<string> &v){
    v.clear(); // delete all vector elements
}

void print_vector(const vector<string> &v){
    for (auto s:v){
        cout << s << " ";
    }
}

int main(){
    int num{10};
    int another_num{20};

    cout << "num before calling pass_by_ref1: " 
        << num << endl;
    pass_by_ref1(another_num);
    cout << "another_num after calling pass_by_ref1: " 
        << another_num << endl;

    string name{"Frank"};
    cout << "\nname before calling pass_by_ref2: " << name << endl;
    pass_by_ref2(name);
    cout << "name after calling pass_by_ref2: " << name << endl;

    vector<string> stooges {"Larry", "Moe", "Curly"};
    cout << "\nstooges before calling pass_by_ref3: ";
    print_vector(stooges);
    pass_by_ref3(stooges);
    cout << "\nstooges after calling pass_by_ref3: ";
    print_vector(stooges);
}
```

# Coding Exercise: Using Pass by Reference - Print a Guest List

In this exercise you will rewrite the previous **_Guest List_** exercise only this time with the use of reference variables.

In this exercise you will create a program that will be used to `print` the `guest list` to an event and then `clear` the `guest list` when the event is over.

Begin by completing the function prototypes `print_guest_list` and `clear_guest_list` which are both `passed three string **reference** variables`. Ensure that the variables cannot be modified within the `print_guest_list` function by using the keyword `const` in the parameter list.

Now that the function prototypes have been declared, at the bottom of the file define both functions.

Both the `print_guest_list` and `clear_guest_list` functions will be passed the `string arguments` `guest_1`, `guest_2`, and `guest_3` which have all been provided to you.

The `print_guest_list` function should `print` the `guest list` in the order of `guest_1`, `guest_2` , `guest_3`, with each entry being printed on a new line. For testing purposes, please ensure that a `newline` is printed after `guest_3` either through the use of `endl`; or the `newline` character `"\n"`. 

The `clear_guest_list` function should replace the string values contained within `guest_1`, `guest_2`, and `guest_3` with the string value `" "`, a single space.

Now, from the function body of `event_guest_list`, make the following function calls in this order:

`print_guest_list`

`clear_guest_list`

`print_guest_list`

passing `guest_1`, `guest_2`, and `guest_3` with each function call.

You can find my solution by clicking on the **solution.txt** file on the left pane. But please make sure you give it a go yourself first, and only check the solution if you really get stuck.

```cpp
#include <iostream>
#include <string>
#include <typeinfo>
using namespace std;

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE THE FUNCTION PROTOTYPES BELOW THIS LINE----

string print_guest_list(            );//----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES
void clear_guest_list(            );//----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES

//----WRITE THE FUNCTION PROTOTYPES ABOVE THIS LINE----
//----DO NOT MODIFY THE CODE BELOW THIS LINE----

void event_guest_list() {

    string guest_1 {"Larry"};
    string guest_2 {"Moe"};
    string guest_3 {"Curly"};

    //----DO NOT MODIFY THE CODE ABOVE THIS LINE----
    //----WRITE THE FUNCTION CALLS BELOW THIS LINE----

    
    
    

    //----WRITE THE FUNCTION CALLS ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
}

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE THE FUNCTION DEFINITION BELOW THIS LINE----

string print_guest_list(            ) {//----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES

    //----WRITE THE FUNCTION BODY BELOW THIS LINE----
    
    
    
    //----WRITE THE FUNCTION BODY ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
    string test_1 = typeid(guest_1).name(), test_2 = typeid(guest_2).name(), test_3 = typeid(guest_3).name();
    return test_1 + test_2 + test_3;
}

//----DO NOT MODIFY THE CODE ABOVE THIS LINE----
//----WRITE THE FUNCTION DEFINITION BELOW THIS LINE----

void clear_guest_list(            ) {//----WRITE THE FUNCTION PARAMETER LIST WITHIN THE PARENTHESES
    
    //----WRITE THE FUNCTION BODY BELOW THIS LINE----
    
    
        
    //----WRITE THE FUNCTION BODY ABOVE THIS LINE----
    //----DO NOT MODIFY THE CODE BELOW THIS LINE----
}
```

