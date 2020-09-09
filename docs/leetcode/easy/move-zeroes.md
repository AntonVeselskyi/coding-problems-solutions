## [Move Zeroes](https://leetcode.com/problems/move-zeroes)

<p>Given an array <code>nums</code>, write a function to move all <code>0</code>&#39;s to the end of it while maintaining the relative order of the non-zero elements.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b> <code>[0,1,0,3,12]</code>
<b>Output:</b> <code>[1,3,12,0,0]</code></pre>

<p><b>Note</b>:</p>

<ol>
	<li>You must do this <b>in-place</b> without making a copy of the array.</li>
	<li>Minimize the total number of operations.</li>
</ol>

## Solutions
#### 🧠 Cpp
```cpp
#include <algorithm>

class Solution {
public:
    void moveZeroes(vector<int>& nums)
    {
        unsigned num0 = std::count(nums.begin(), nums.end(), 0);
        std::remove_if(nums.begin(), nums.end(), [](int a){if(a == 0) return true; return false;});
        std::fill(nums.end() - num0, nums.end(), 0);
    }
};
```
