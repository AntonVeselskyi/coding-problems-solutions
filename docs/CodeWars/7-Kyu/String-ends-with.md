## [String ends with?](https://www.codewars.com/kata/51f2d1cafc9c0f745c00037d)

Complete the solution so that it returns true if the first argument(string) passed in ends with the 2nd argument (also a string). 

Examples:

```javascript
solution('abc', 'bc') // returns true
solution('abc', 'd') // returns false
```
```coffeescript
solution('abc', 'bc') # returns true
solution('abc', 'd') # returns false
```
```python
solution('abc', 'bc') # returns true
solution('abc', 'd') # returns false
```
```go
solution("abc", "bc") // returns true
solution("abc", "d") // returns false
```
```prolog
solution("abc", "bc"). % match
\+ solution("abc", "d"). % no match
```

## Solutions
#### 🐍 Python
```python
def solution(str, e):
    return str[-len(e):] == e
```
#### 👴 C
```c
#include <string.h>

char solution(const char *str, const char *end)
{
    int bias = strlen(str) - strlen(end);
    return bias < 0 ? 0 : !strcmp( (str+bias), end );
}
```
