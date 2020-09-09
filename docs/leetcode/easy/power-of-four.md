## [Power of Four](https://leetcode.com/problems/power-of-four)

<p>Given an integer (signed 32 bits), write a function to check whether it is a power of 4.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">16</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">5</span>
<strong>Output: </strong><span id="example-output-2">false</span></pre>
</div>

<p><b>Follow up</b>: Could you solve it without loops/recursion?</p>

## Solutions
#### 🧠 Cpp
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
