```cpp
if (expr)
	statement;
```

- If the expression is true then execute the statement.
- If the expression is false then skip the statement.

### Example 1:

![](Programming/Section%209%20Controlling%20Program%20Flow/Pictures/if%20Statement%20Example%201.png)

### Example 2:

```cpp
if (selection == 'A')
	cout << "You selected A";

if (num > 10)
	cout << "num is greater than 10";

if (health < 100 && playe_healed)
	health = 100;
```

## Block Statement:

![[Programming/Section 9 Controlling Program Flow/Pictures/Block Statement.png]]
```cpp
{
	//variable declarations
	statement1;
	statement2;
	- - -
}
```

- Create a block of code by including more than one statement in code block { }.
- Blocks can also contain variable declarations.
- These variables are visible only within the block - local scope.

## Exercise 1:

### Condition:

![[Programming/Section 9 Controlling Program Flow/Pictures/if Statement Exercise 1 Condition.png]]
1. Greater than 10.
2. Less than 100.
3. Between 10 and 100.
4. Equal to 10 or 100.

```cpp
int main() {
    int num{};
    const int MIN{10};
    const int MAX{100};

    cout << "Enter a number between " << MIN << " and " << MAX << " : " << 
    endl;
    cin >> num;

    if (num >= MIN) {
        cout << "\n================== If Statement 1 ==================" <<
        endl;
        cout << num << " is greater than or equal to " << MIN << endl;

        int diff {num - MIN};                                                            // Only in scope to this if Statement.
        cout << num << " is " << diff << " greater than " << MIN << endl;
    }

    if (num <= MAX) {
        cout << "\n================== If Statement 2 ==================" <<
        endl;
        cout << num << " is less than or equal to " << MAX << endl;

        int diff {MAX-num};
        cout << num << " is " << diff << " less than " << MAX << endl;
    }

    if (num >= MIN && num <= MAX) {
        cout << "\n================== If Statement 3 ==================" << 
        endl;
        cout << num << " is in range " << endl;
        cout << " This means statements 1 and 2 must also display";
    }

    if (num == MIN || num == MAX) {
        cout << "\n================== If Statement 4 ==================" << 
        endl;
        cout << num << " is right on a boundary " << endl;
        cout << "This means all 4 statements display" << endl;
    }

}
```

```
Enter a number between 10 and 100 : 
10

================== If Statement 1 ==================
10 is greater than or equal to 10
10 is 0 greater than 10

================== If Statement 2 ==================
10 is less than or equal to 100
10 is 90 less than 100

================== If Statement 3 ==================
10 is in range
 This means statements 1 and 2 must also display
================== If Statement 4 ==================
10 is right on a boundary
This means all 4 statements display
```

