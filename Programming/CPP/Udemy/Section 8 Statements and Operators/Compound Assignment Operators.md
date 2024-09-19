# op=

| Operator | Example      | Meaning                |
| -------- | ------------ | ---------------------- |
| +=       | lhs += rhs;  | lhs = lhs + (rhs);     |
| -=       | lhs -= rhs;  | lhs = lhs - (rhs);     |
| *=       | lhs *= rhs;  | lhs = lhs * (rhs);     |
| /=       | lhs /= rhs;  | lhs = lhs / (rhs);     |
| %=       | lhs %= rhs;  | lhs = lhs % (rhs);     |
| >>=      | lhs >>= rhs; | lhs = lhs >> (rhs);    |
| <<=      | lhs <<= rhs; | lhs = lhs << (rhs);    |
| &=       | lhs &= rhs;  | lhs = lhs & (rhs);     |
| ^=       | lhs ^= rhs;  | lhs = lhs ^ (rhs);     |
| \|=      | lhs \|= rhs; |  lhs = lhs \| (rhs);   |
# Examples

```cpp
lhs op= rhs; lhs =  // lhs op (rhs)

a += 1;             // a = a + 1;
a /= 5;             // a = a / 5;
a *= b + c;         // a = a * (b + c);

cost += items * tax // cost = cost + (items * tax); 
```

## Note:

Think of the **right hand side** as always being inside parenthesis "()" and you'll always get it right. 