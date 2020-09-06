# Excel Sheet Column Number

## [Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number)

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

```text

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
```

**Example 1:**

```text

Input: "A"
Output: 1
```

**Example 2:**

```text

Input: "AB"
Output: 28
```

**Example 3:**

```
 Input: "ZY" Output: 701 
```

**Constraints:**

* `1 <= s.length <= 7`
* `s` consists only of uppercase English letters.
* `s` is between "A" and "FXSHRXW".

## Solutions

### 🧠 Cpp

```cpp
class Solution {
public:
    int titleToNumber(string s)
    {
        int res = 0;
        int index = 0;
        for(auto riter = s.rbegin(); riter != s.rend(); ++riter, ++index)
            res+= (*riter-'A'+1)*std::pow(26,index);
        return res;
    }
};
```

