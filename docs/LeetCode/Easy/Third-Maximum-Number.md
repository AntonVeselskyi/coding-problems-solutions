## [Third Maximum Number](https://leetcode.com/problems/third-maximum-number)

<p>Given a <b>non-empty</b> array of integers, return the <b>third</b> maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> [3, 2, 1]

<b>Output:</b> 1

<b>Explanation:</b> The third maximum is 1.
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> [1, 2]

<b>Output:</b> 2

<b>Explanation:</b> The third maximum does not exist, so the maximum (2) is returned instead.
</pre>
</p>

<p><b>Example 3:</b><br />
<pre>
<b>Input:</b> [2, 2, 3, 1]

<b>Output:</b> 1

<b>Explanation:</b> Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
</pre>
</p>

## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    int thirdMax(vector<int> nums)
    {
        std::sort(nums.begin(), nums.end());
        nums.erase(std::unique(nums.begin(), nums.end()), nums.end());

        const size_t uniq_size = nums.size();
        if(uniq_size < 3)
            return nums[uniq_size-1];
        else
        {
            return nums[uniq_size-3];
        }
    }
};
```
