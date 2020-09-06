# Third Maximum Number

## [Third Maximum Number](https://leetcode.com/problems/third-maximum-number)

Given a **non-empty** array of integers, return the **third** maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O\(n\).

**Example 1:**  


```text

Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
```

**Example 2:**  


```text

Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```

**Example 3:**  


```text

Input: [2, 2, 3, 1]

Output: 1

Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```

## Solutions

### 🧠 Cpp

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
            return *std::max_element(nums.begin(), nums.end());
        else
        {
            return nums[uniq_size-3];
        }
    }
};
```

