# Introduction

- Addition `+`
- Subtraction `-`
- Multiplication `*`
- Division `/`
- Exponent `**`

**Note:** When dividing the resulting data type is always floating point regardless of whether decimal values are present after the division has taken place. If you don't want that you can use the `//` division operator to convert the output back to an integer after the division has taken place but note that this will truncate the decimal.

# Priority

BODMAS applies. The order of operations for these operators are as follows:

`()` -> `**` -> `*` OR `/` -> `+` OR `-`

For operations that are at the same level of priority, they will be completed from left to right. 