# XOR Operation in an Array

## [XOR Operation in an Array](https://leetcode.com/problems/xor-operation-in-an-array)

Given an integer `n` and an integer `start`.

Define an array `nums` where `nums[i] = start + 2*i` \(0-indexed\) and `n == nums.length`.

Return the bitwise XOR of all elements of `nums`.

**Example 1:**

```text

Input: n = 5, start = 0
Output: 8
Explanation: Array nums is equal to [0, 2, 4, 6, 8] where (0 ^ 2 ^ 4 ^ 6 ^ 8) = 8.
Where "^" corresponds to bitwise XOR operator.
```

**Example 2:**

```text

Input: n = 4, start = 3
Output: 8
Explanation: Array nums is equal to [3, 5, 7, 9] where (3 ^ 5 ^ 7 ^ 9) = 8.
```

**Example 3:**

```text

Input: n = 1, start = 7
Output: 7
```

**Example 4:**

```text

Input: n = 10, start = 5
Output: 2
```

**Constraints:**

* `1 <= n <= 1000`
* `0 <= start <= 1000`
* `n == nums.length`

## Solutions

### 🧠 Cpp

```cpp
class Solution
{
public:
    int xorOperation(int n, int start)
    {
        int res = start;
        for(size_t i = 1 ; i < n; ++i)
            res ^= start+2*i;
        return res;
    }
};
```
