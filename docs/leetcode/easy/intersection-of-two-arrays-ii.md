# Intersection of Two Arrays II

## [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii)

Given two arrays, write a function to compute their intersection.

**Example 1:**

```text

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]
```

**Example 2:**

```text

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [4,9]
```

**Note:**

* Each element in the result should appear as many times as it shows in both arrays.
* The result can be in any order.

**Follow up:**

* What if the given array is already sorted? How would you optimize your algorithm?
* What if nums1's size is small compared to nums2's size? Which algorithm is better?
* What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

## Solutions

### 🧠 Cpp

```cpp
#include <algorithm>
using std::count;

class Solution
{
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2)
    {
        bool is_firstbigger = nums1.size() > nums2.size();
        vector<int> res,
            &big = is_firstbigger ? nums1 : nums2,
            &small = is_firstbigger ? nums2 : nums1;



        for(int i = 0; i < small.size(); ++i)
        {
            int b_element = small[i],  
                count_in_big = count(big.begin(), big.end(), b_element);

            if(count_in_big > 0 && count(res.begin(), res.end(), b_element) == 0)
            {
                int count_in_small = count(small.begin(), small.end(), b_element);
                res.insert(res.begin(), std::min(count_in_big, count_in_small), b_element);
            }   
        }

        return res;
    }
};
```

