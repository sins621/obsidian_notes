

| Operator   | Meaning     |
| ---------- | ----------- |
| not<br>!   | negation    |
| and<br>&&  | logical and |
| or<br>\|\| | logical or  |
# Expression Tables:
## not (!)

| expression<br>        a | not a<br>   !a |
| ----------------------- | -------------- |
| true                    | false          |
| false                   | true           |
## and (&&)

| expression<br>        a | expression<br>        b | a and b<br>a && b |
| ----------------------- | ----------------------- | ----------------- |
| true                    | true                    | true              |
| true                    | false                   | false             |
| false                   | true                    | false             |
| false                   | false                   | false             |

## or (||)

| expression<br>        a | expression<br>        b | a or b<br>a \|\| b |
| ----------------------- | ----------------------- | ------------------ |
| true                    | true                    | true               |
| true                    | false                   | true               |
| false                   | true                    | true               |
| false                   | false                   | false              |
# Precedence

- `not` has higher precedence than `and`
- `and` has higher precedence than `or`

- `not` is a unary operator
- `and` and `or` are binary operators

# Examples:

```cpp
num1 >= 10 && num1 < 20
num1 <= 10 || num1 >= 20

!is_raining && temperature > 32.0

is_raining || is_raining

temperature > 100 && is_humid || is_raining
```

# Short-Circuit Evaluation

- When evaluating a logical expression C++ stops as soon as the result is known

```cpp
expr1 && expr2 && expr3
expr1 || expr2 || expr3
```

# Example: Bounds Checking
## Inside Bounds:
![](Programming/Section%208%20Statements%20and%20Operators/Pictures/Sectio8_LogicalOperators_BoundsChecking.png)

### Output (true):

```
Enter an integer - The bounds are 10 and 20:
15
15 is between 10 and 20 : true
```

### Output (false):

```
Enter an integer - The bounds are 10 and 20:
7
7 is between 10 and 20 : false
```

## Outside Bounds:

![[Programming/Section 8 Statements and Operators/Pictures/Section8_LogicalOperators_OutOfBounds.png]]

## Output:

```
Enter an integer - The bounds are 10 and 20:
15
15 is outside 10 and 20 : false
```

## On Bounds:

![[Programming/Section 8 Statements and Operators/Pictures/Section8_LogicalOperators_OnBounds.png]]

## Output:

```
Enter an integer - the bounds are 10 and 20 : 20
20 is one of the bounds which are 10 and 20 : true
```

# Example: To Wear a Coat or Not

## AND

```cpp
bool wear_coat{false};

double temperature{};

int wind_speed{};

const int WIND_SPEED_FOR_COAT{25};       // wind over this value requires a coat
const double TEMPERATURE_FOR_COAT{45};   // temperature below this value requires a coat

cout << "\nEnter the current temperature in (F): ";
cin >> temperature;
cout << "Enter windspeed in (mph): ";
cin >> wind_speed;

// Require a coat if BOTH the windspeed is too high AND temperature is too low
wear_coat = (temperature < TEMPERATURE_FOR_COAT && wind_speed > WIND_SPEED_FOR_COAT);
cout << "Do you need to wear a coat using AND? : " << wear_coat << endl;
```

### Output: Both Fulfilled

```
Enter the current temperature in (F): 35
Enter windspeed in (mph): 30
Do you need to wear a coat using AND? : true
```

### Output: Only One Fulfilled

```
Enter the current temperature in (F): 35
Enter windspeed in (mph): 20
Do you need to wear a coat using AND? : false
```

## OR:

```cpp
// Require a coat if BOTH the windspeed is too high OR temperature is too low
wear_coat = (temperature < TEMPERATURE_FOR_COAT || wind_speed > WIND_SPEED_FOR_COAT);
cout << "Do you need to wear a coat using AND? : " << wear_coat << endl;
```

### Output: Only One Fulfilled

```
Enter the current temperature in (F): 40
Enter windspeed in (mph): 20
Do you need to wear a coat using AND? : true
```

