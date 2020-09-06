# Power of Four

## [Power of Four](https://leetcode.com/problems/power-of-four)

Given an integer \(signed 32 bits\), write a function to check whether it is a power of 4.

**Example 1:**

```text

Input: 16
Output: true
```

**Example 2:**

```text

Input: 5
Output: false
```

**Follow up**: Could you solve it without loops/recursion?

## Solutions

### 🧠 Cpp

```cpp
#include <stdint.h>

class Solution
{
public:
    bool isPowerOfFour(unsigned num) 
    {
      return (__builtin_popcount(num) == 1) && (num & 0b01010101010101010101010101010101);
        // return num > 0 && (num & (num - 1)) == 0 && num & 0x55555555;
//         if (num == 1) // case for power of 0
//             return true;

//         for (uint32_t i = 1; (i <<= 2);)
//             if (i == num)
//                 return true;
//         return false;
    }
};
```

