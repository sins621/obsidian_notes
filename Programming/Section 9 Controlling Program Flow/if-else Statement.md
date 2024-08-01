```cpp
if (expr)
	statement1;
else
	statement2;
```

- If the expression is true then execute statement1

- if the expression is false then execute statement2

![[if-else Statement Example 1.png]]
```cpp
if (num > 10)
	cout << "num is greater than 10";
else
	cout << "num is NOT greater than 10";

if (health < 100 && heal_player)
	health = 100;
else
	++health;
```

![[if-else Statement Example 2.png]]
## if-else-if construct

```cpp
if (score > 90)
	cout << "A";
else if (score < 80)
	cout << "B";
else if (score > 70)
	cout << "C";
else if (score > 60)
	cout << "D";
else
	cout << "F";           // all others must be F

cout << "Done";
```

