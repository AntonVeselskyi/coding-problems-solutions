# Two Sum

## [Two Sum](https://leetcode.com/problems/two-sum)

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have _**exactly**_ **one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

```text

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```text

Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```text

Input: nums = [3,3], target = 6
Output: [0,1]
```

**Constraints:**

* `2 <= nums.length <= 105`
* `-109 <= nums[i] <= 109`
* `-109 <= target <= 109`
* **Only one valid answer exists.**

## Solutions

### 🧠 Cpp

```cpp
#include <algorithm>

class Solution
{
public:
    vector<int> twoSum(vector<int> nums, int target) 
    {
        std::remove_if(nums.begin(), nums.end(), [target](int i){ return i > target;});
        for(auto el = nums.begin(); el != nums.end(); el++)
            for(auto el2 = el; ++el2 != nums.end();)
                if(*el + *el2 == target)
                    return {(int)(el-nums.begin()),(int)(el2-nums.begin())};
        return {};
    }
};
```

