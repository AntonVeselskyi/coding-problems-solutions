# Median of Two Sorted Arrays

## [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays)

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.

**Follow up:** The overall run time complexity should be `O(log (m+n))`.

**Example 1:**

```text

Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

**Example 2:**

```text

Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

**Example 3:**

```text

Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000
```

**Example 4:**

```text

Input: nums1 = [], nums2 = [1]
Output: 1.00000
```

**Example 5:**

```text

Input: nums1 = [2], nums2 = []
Output: 2.00000
```

**Constraints:**

* `nums1.length == m`
* `nums2.length == n`
* `0 <= m <= 1000`
* `0 <= n <= 1000`
* `1 <= m + n <= 2000`

## Solutions

### 🧠 Cpp

```cpp
#include <algorithm>

class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2)
    {
        int target_size = nums1.size() + nums2.size();
        vector<int> combined(target_size);

        // SOLUTION A - 48 ms    89.6 MB
        copy(nums1.begin(), nums1.end(), combined.begin());
        copy(nums2.begin(), nums2.end(), combined.begin()+nums1.size());
        sort(combined.begin(),combined.end());


        // SOLUTION B - 124 ms    89.6 MB      
//         for(int i = 0, ni1 = 0, ni2 = 0; i < target_size; ++i)
//         {
//             if(ni1 != nums1.size())
//             if(ni2 == nums2.size() || nums1[ni1] <= nums2[ni2])
//             {
//                 combined[i] = nums1[ni1++];
//                 continue;
//             }

//             if(ni2 != nums2.size())
//             if(ni1 == nums1.size() || nums2[ni2] <= nums1[ni1])
//             {
//                 combined[i] = nums2[ni2++];
//                 continue;
//             }
//         }

        if(target_size % 2)
            return combined[(target_size/2)];
        else
            return (combined[(target_size/2)-1] + combined[(target_size/2)]) / 2.f;


    }
};
```

