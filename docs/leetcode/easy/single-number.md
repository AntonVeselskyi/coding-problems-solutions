# Single Number

## [Single Number](https://leetcode.com/problems/single-number)

Given a **non-empty** array of integers, every element appears _twice_ except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

```text

Input: [2,2,1]
Output: 1
```

**Example 2:**

```text

Input: [4,1,2,1,2]
Output: 4
```

## Solutions

### 🧠 Cpp

```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums)
    {
        for(int i=0; i < nums.size(); ++i)
        {
            for(int j=0; ; ++j)
                if(nums[i] == nums[j] && i != j)
                    break;
                else if (j == nums.size()-1)
                    return nums[i]; 
        }

        return 0;
    }
};
```

