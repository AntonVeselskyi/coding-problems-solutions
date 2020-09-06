# Number of Good Pairs

## [Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs)

Given an array of integers `nums`.

A pair `(i,j)` is called _good_ if `nums[i]` == `nums[j]` and `i` &lt; `j`.

Return the number of _good_ pairs.

**Example 1:**

```text

Input: nums = [1,2,3,1,1,3]
Output: 4
Explanation: There are 4 good pairs (0,3), (0,4), (3,4), (2,5) 0-indexed.
```

**Example 2:**

```text

Input: nums = [1,1,1,1]
Output: 6
Explanation: Each pair in the array are good.
```

**Example 3:**

```text

Input: nums = [1,2,3]
Output: 0
```

**Constraints:**

* `1 <= nums.length <= 100`
* `1 <= nums[i] <= 100`

## Solutions

### 🧠 Cpp

```cpp
class Solution {
public:
    int numIdenticalPairs(vector<int>& nums)
    {
        size_t counter = 0;
        for(auto iter = nums.begin(); iter != nums.end(); ++iter)
            counter += std::count(std::next(iter), nums.end(), *iter);

        return counter;

    }
};
```

