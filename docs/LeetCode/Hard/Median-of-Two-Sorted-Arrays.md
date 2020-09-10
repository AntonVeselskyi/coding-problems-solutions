## [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays)

<p>Given two sorted arrays <code>nums1</code> and <code>nums2</code> of size <code>m</code> and <code>n</code> respectively, return <strong>the median</strong> of the two sorted arrays.</p>

<p><strong>Follow up:</strong> The overall run time complexity should be <code>O(log (m+n))</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,3], nums2 = [2]
<strong>Output:</strong> 2.00000
<strong>Explanation:</strong> merged array = [1,2,3] and median is 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,2], nums2 = [3,4]
<strong>Output:</strong> 2.50000
<strong>Explanation:</strong> merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [0,0], nums2 = [0,0]
<strong>Output:</strong> 0.00000
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [], nums2 = [1]
<strong>Output:</strong> 1.00000
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [2], nums2 = []
<strong>Output:</strong> 2.00000
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>nums1.length == m</code></li>
	<li><code>nums2.length == n</code></li>
	<li><code>0 &lt;= m &lt;= 1000</code></li>
	<li><code>0 &lt;= n &lt;= 1000</code></li>
	<li><code>1 &lt;= m + n &lt;= 2000</code></li>
	<li><code>-10<sup>6</sup> &lt;= nums1[i], nums2[i] &lt;= 10<sup>6</sup></code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
#include <algorithm>

class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2)
    {
        int target_size = nums1.size() + nums2.size();
        vector<int> combined(target_size);

        // SOLUTION A - 48 ms	89.6 MB
        copy(nums1.begin(), nums1.end(), combined.begin());
        copy(nums2.begin(), nums2.end(), combined.begin()+nums1.size());
        sort(combined.begin(),combined.end());
        

        // SOLUTION B - 124 ms	89.6 MB      
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
