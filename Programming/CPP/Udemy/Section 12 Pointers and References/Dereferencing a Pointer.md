# Introduction

Access the data we're pointing to - dereferencing a pointer.

- If `score_ptr` is a pointer and has a valid address
- Then you can access the data at the address contained in the `score_ptr` using the dereferencing operator *

In order to access the data that a pointer is pointing to we need to follow the pointer to where it's pointing, this is called **dereferencing the pointer**. 

Let's say that `score_ptr` is a pointer to an integer and it has a valid address, then in order to access the integer that `score_ptr` is pointing to we use the dereferencing or indirection operator which is the asterisk. 

The asterisk? Didn't we just use the asterisk to declare the pointer? Yes, and lot's of people over the years have been critical of C++'s choice to use the asterisk to both declare and dereference the pointer, but it is what it is and once we understand how all this works it isn't confusing at all.

Let's take a look at the example:

```cpp nums
int score{100};
int *score_ptr{&score};

cout << *score_ptr << endl;                 // 100

*score_ptr = 200;
cout << *score_ptr << endl;                 // 200
cout << score << endl;                      // 200
```

First we declare `score` to be an integer and then initialize it to 100, then we declare `*score_ptr` to be a pointer to an integer and then initialize it to the address of `score`. Now `score_ptr` points to `score`, if we want to get to `score` via the pointer then we must dereference the pointer. 

Notice that in the first output statement we're using the dereference operator on `score_ptr`, this follows the pointer and gives us what it points to. In this case we display 100 since `score_ptr` points to `score`. 

When we dereference a pointer on the left hand side of an assignment statement this results in an L value or the address of what `score_ptr` is pointing to which in this case is score. So we store 200 in that address which is the address of `score`. So now we just change the value of `score` in indirectly via the pointer. Notice the syntax makes sense, we use the asterisk to declare the pointer and then once the pointer is declared the asterisk is used to dereference it.

Let's see another example:

# Accessing the Data We're Pointing to:

## Int & Double Example:

In this example we declare two doubles `high_temp` and `low_temp` and initialize them to 100.7 and 37.4, we also declare `temp_ptr` as a pointer to a double and initialize it to point to `high_temp`. So if we have a pointer and want what it points to we dereference the pointer. 

```cpp nums
double high_temp {100.7};
double low_temp{37.4};
double *temp_ptr{&high_temp};

cout << *temp_ptr << endl;             // 100.7

temp_ptr = &low_temp;

cout << *temp_ptr << endl;             // 37.4
```

That's exactly what we're doing in the first output statement, we're following or dereferencing `temp_ptr` which gives us what it points to and in this case we display 100.7. Now in the assignment statement we're storing the address of `low_temp` to `temp_ptr` so now `temp_ptr` is pointing to `low_temp` and again if we want the `low_temp` we dereference `temp_ptr` and and that gets us to where it's pointing. 

So far we've used ints an doubles but the data type can be anything.

## String Example:

In this case `name` is a c++ string object with the value "Frank" and `string_ptr` is a pointer to a string and we initialize it to point to `name`. If we dereference `string_ptr` as in the first output statement we display "Frank". If `name` then changes to "James" and we execute the same output statement then we display "James".

```cpp nums
string name {"Frank"};

string *string_ptr{&name};

cout << *string_ptr << endl;               // Frank

name = "James";

cout << *string_ptr << endl;               // James
```

Let's head over to the IDE and we'll see some more examples of dereferencing pointers in live code:

# Examples in the IDE:


```cpp nums
#include <iostream>
#include<string>
#include<vector>

using namespace std;

int main(){
    int score {100};
    int *score_ptr{&score};

    cout << *score_ptr << endl;                 // 100

    *score_ptr = 200;

    cout << *score_ptr << endl;                 // 200
    cout << score << endl;                      // 200

    cout << "\n-----------------------" << endl;
    double high_temp{100.7};
    double low_temp{37.4};
    double *temp_ptr{&high_temp};

    cout << *temp_ptr << endl;                 // 100.7
    temp_ptr = &low_temp;
    cout << *temp_ptr << endl;                 // 37.4

    cout << "\n-----------------------" << endl;

    string name{"Frank"};
    string *string_ptr{&name};

    cout << *string_ptr << endl;                  // Frank 
    name = "James";
    cout << *string_ptr << endl;                  // James

    cout << "\n-----------------------" << endl;
    vector<string> stooges{"Larry", "Moe", "Curly"};
    vector<string> *vector_ptr{nullptr};

    vector_ptr = &stooges;

    cout << "First Stooge: " << (*vector_ptr).at(0) << endl;

    cout << "Stooges: ";
    for (auto stooge: *vector_ptr)
        cout << stooge << " ";
    cout << endl;
}
```

## Output:

```
100
200
200

-----------------------
100.7
37.4

-----------------------
Frank
James

-----------------------
First Stooge: Larry
Stooges: Larry Moe Curly
```