expr1 **OP** expr2

| Operator | Meaning                      |
| -------- | ---------------------------- |
| >        | greater than                 |
| >=       | greater than or equal to     |
| <        | less than                    |
| <=       | less than or equal to        |
| <=>      | three-way comparison (c++20) |
### <=> Operator

This operator compares two expressions and evaluates to:

- 0 if they are equal
- less than 0 if the left hand side is greater than the right hand side
- greater than 0 if the right hand side is greater than the left hand side

## Example 1:

```cpp
# include <iostream>

using namespace std;

int main (){
    
    int num1{},num2{};
    
    cout << boolalpha;
    
    cout << "Enter 2 integers seperated by space " << endl;
    
    cin >> num1 >> num2;


    cout << num1 << " > " << num2 << " : " << (num1 > num2) << endl;
    
    cout << num1 << " >= " << num2 << " : " << (num1 >= num2) << endl;
    
    cout << num1 << " < " << num2 << " : " << (num1 < num2) << endl;
    
    cout << num1 << " <= " << num2 << " : " << (num1 <= num2) << endl;
}
```

### Input:

```
1 2
```
### Output:

```
1 > 2 : false
1 >= 2 : false
1 < 2 : true
1 <= 2 : true
```
![](Programming/Section%208%20Statements%20and%20Operators/Pictures/Section8_Figure1.png)

## boolalpha:

using:

```cpp
cout << boolalpha
```

The output for the comparisons that would normally return **0** and **1** will now return **true** or **false**.

## Example 2:

```cpp
int main (){

    int num1{},num2{};
    cout << boolalpha;
    const int LOWER{10};
    const int UPPER{20};

    cout << "\nEnter an integer that is greater than " << LOWER << " : ";

    cin >> num1;

    cout << "num1" << " > " << LOWER << " is " << (num1 > LOWER) << endl;

    cout << "\nEnter an integer that is less than or equal to " << UPPER << " : ";

    cin >> num2;

    cout << "num2" << " <= " << UPPER << " is " << (num2 <= UPPER) << endl;

}
```

### Input:

```
11

20
```
### Output:

```
Enter an integer that is greater than 10 : 11
num1 > 10 is true

Enter an integer that is less than or equal to 20 : 20
num2 <= 20 is true
```

![[Programming/Section 8 Statements and Operators/Pictures/Pasted image 20240509005214.png]]
