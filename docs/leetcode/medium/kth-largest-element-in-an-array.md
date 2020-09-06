# Kth Largest Element in an Array

## [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array)

Find the **k**th largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

**Example 1:**

```text

Input: [3,2,1,5,6,4] and k = 2
Output: 5
```

**Example 2:**

```text

Input: [3,2,3,1,2,4,5,5,6] and k = 4
Output: 4
```

**Note:**  
 You may assume k is always valid, 1 ≤ k ≤ array's length.

## Solutions

### 🧠 Cpp

```cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k)
    {
        std::sort(nums.begin(), nums.end());
        return nums[nums.size()-k];
    }
};
```

