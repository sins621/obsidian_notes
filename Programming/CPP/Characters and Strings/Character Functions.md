# `#include <cctype>`

The `cctype` includes very simple and very useful functions that allow the testing of various properties as well as the conversion of characters from upper to lower or lower to upper case.

```cpp
#include <cctype>

function_name(char)
```

- Functions for Testing Characters
- Functions for Converting Character Case

# Testing Characters

| Code         | Explanation                          |
| ------------ | ------------------------------------ |
| `isalpha(c)` | True if c is a letter                |
| `isalnum(c)` | True if c is a letter or digit       |
| `isdigit(c)` | True if c is a digit                 |
| `islower(c)` | True if c is lowercase letter        |
| `isprint(c)` | True if c is a printable character   |
| `ispunct(c)` | True if c is a punctuation character |
| `isupper(c)` | True if c is an uppercase letter     |
| `isspace(c)` | True if c is whitespace              |
# Converting Characters

| Code         | Explanation            |
| ------------ | ---------------------- |
| `tolower(c)` | returns lowercase of c |
| `toupper(c)` | returns uppercase of c |

