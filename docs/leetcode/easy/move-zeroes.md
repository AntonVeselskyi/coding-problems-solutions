# Move Zeroes

## [Move Zeroes](https://leetcode.com/problems/move-zeroes)

Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Example:**

```text

Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Note**:

1. You must do this **in-place** without making a copy of the array.
2. Minimize the total number of operations.

## Solutions

### 🧠 Cpp

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

