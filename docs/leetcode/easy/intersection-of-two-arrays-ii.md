## [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii)

<p>Given two arrays, write a function to compute their intersection.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>nums1 = <span id="example-input-1-1">[1,2,2,1]</span>, nums2 = <span id="example-input-1-2">[2,2]</span>
<strong>Output: </strong><span id="example-output-1">[2,2]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>nums1 = <span id="example-input-2-1">[4,9,5]</span>, nums2 = <span id="example-input-2-2">[9,4,9,8,4]</span>
<strong>Output: </strong><span id="example-output-2">[4,9]</span></pre>
</div>

<p><b>Note:</b></p>

<ul>
	<li>Each element in the result should appear as many times as it shows in both arrays.</li>
	<li>The result can be in any order.</li>
</ul>

<p><b>Follow up:</b></p>

<ul>
	<li>What if the given array is already sorted? How would you optimize your algorithm?</li>
	<li>What if <i>nums1</i>&#39;s size is small compared to <i>nums2</i>&#39;s size? Which algorithm is better?</li>
	<li>What if elements of <i>nums2</i> are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?</li>
</ul>


## Solutions
#### 🧠 Cpp
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
