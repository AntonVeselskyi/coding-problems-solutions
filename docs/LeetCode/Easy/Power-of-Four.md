## [Power of Four](https://leetcode.com/problems/power-of-four)

<p>Given an integer <code>n</code>, return <em><code>true</code> if it is a power of four. Otherwise, return <code>false</code></em>.</p>

<p>An integer <code>n</code> is a power of four, if there exists an integer <code>x</code> such that <code>n == 4<sup>x</sup></code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 16
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> n = 5
<strong>Output:</strong> false
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> true
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup> &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you solve it without loops/recursion?

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
