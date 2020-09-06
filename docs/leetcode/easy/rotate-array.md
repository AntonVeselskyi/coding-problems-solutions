# Rotate Array

## [Rotate Array](https://leetcode.com/problems/rotate-array)

Given an array, rotate the array to the right by _k_ steps, where _k_ is non-negative.

**Follow up:**

* Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
* Could you do it in-place with O\(1\) extra space?

**Example 1:**

```text

Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```

**Example 2:**

```text

Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```

**Constraints:**

* `1 <= nums.length <= 2 * 10^4`
* It's guaranteed that `nums[i]` fits in a 32 bit-signed integer.
* `k >= 0`

## Solutions

### 🧠 Cpp

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

