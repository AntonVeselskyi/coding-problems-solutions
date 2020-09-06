# Contains Duplicate

## [Contains Duplicate](https://leetcode.com/problems/contains-duplicate)

Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

**Example 1:**

```text

Input: [1,2,3,1]
Output: true
```

**Example 2:**

```text

Input: [1,2,3,4]
Output: false
```

**Example 3:**

```text

Input: [1,1,1,3,3,4,3,2,4,2]
Output: true
```

## Solutions

### 🧠 Cpp

```cpp
#include <algorithm>

class Solution {
public:
    bool containsDuplicate(vector<int> nums)
    {
        std::sort(nums.begin(), nums.end());

        if(
            nums.size()
            ==
            std::distance( nums.begin(), std::unique(nums.begin(), nums.end()) )
        )
            return false;
        else
            return true;
    }
};
```

