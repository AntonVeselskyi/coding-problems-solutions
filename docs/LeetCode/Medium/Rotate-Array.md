## [Rotate Array](https://leetcode.com/problems/rotate-array)

<p>Given an array, rotate the array to the right by <em>k</em> steps, where&nbsp;<em>k</em>&nbsp;is non-negative.</p>

<p><strong>Follow up:</strong></p>

<ul>
	<li>Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.</li>
	<li>Could you do it in-place with O(1) extra space?</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5,6,7], k = 3
<strong>Output:</strong> [5,6,7,1,2,3,4]
<strong>Explanation:</strong>
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,-100,3,99], k = 2
<strong>Output:</strong> [3,99,-1,-100]
<strong>Explanation:</strong> 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2 * 10^4</code></li>
	<li>It&#39;s guaranteed that <code>nums[i]</code> fits in a 32 bit-signed integer.</li>
	<li><code>k &gt;= 0</code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
#include <iterator>
#include <utility>
#define mmi std::make_move_iterator

class Solution {
public:
    void rotate(vector<int>& nums, int k)
    {
        if(nums.size() <= 1)
            return;
        if(k > nums.size())
            k -= nums.size();
        
        vector<int> right_chunk(nums.end()-k, nums.end());
        //mmi is hack after using mmi nums is not valid
        right_chunk.insert(right_chunk.end(), mmi(nums.begin()), mmi(nums.end()-k));
        nums = std::move(right_chunk);
    }
};
```
