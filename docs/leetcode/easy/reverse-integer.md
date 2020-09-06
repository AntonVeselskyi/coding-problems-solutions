# Reverse Integer

## [Reverse Integer](https://leetcode.com/problems/reverse-integer)

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**

```text

Input: 123
Output: 321
```

**Example 2:**

```text

Input: -123
Output: -321
```

**Example 3:**

```text

Input: 120
Output: 21
```

**Note:**  
 Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: \[−231,  231 − 1\]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

## Solutions

### 🧠 Cpp

```cpp
class Solution {
public:
    int reverse(int x)
    {
        bool is_neg = x < 0;
        std::string num = std::to_string(x);
        std::reverse(num.begin()+is_neg, num.end());

        long res = std::atol(num.c_str());
        return res > numeric_limits<int>::max() || res < numeric_limits<int>::min() ? 
               0  : res;
    }
};
```

