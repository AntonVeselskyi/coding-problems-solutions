## [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array)

<p>Given two sorted integer arrays <code>nums1</code> and <code>nums2</code>, merge <code>nums2</code> into <code>nums1</code> as one sorted array.</p>

<p>The number of elements initialized in <code>nums1</code> and <code>nums2</code> are <code>m</code> and <code>n</code> respectively. You may assume that <code>nums1</code> has enough space (size that is&nbsp;equal to <code>m + n</code>) to hold additional elements from <code>nums2</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
<strong>Output:</strong> [1,2,2,3,5,6]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums1 = [1], m = 1, nums2 = [], n = 0
<strong>Output:</strong> [1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n, m &lt;= 200</code></li>
	<li><code>1 &lt;= n + m &lt;= 200</code></li>
	<li><code>nums1.length == m + n</code></li>
	<li><code>nums2.length == n</code></li>
	<li><code>-10<sup>9</sup> &lt;= nums1[i], nums2[i] &lt;= 10<sup>9</sup></code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n)
    {
        if(!n)
            return;
        if(!m)
        {
            nums1 = nums2;
            return;
        }

        //merge two sorted arrays in one
        auto n1_iter = nums1.begin(),
             n1_end = n1_iter + m,
             n2_iter = nums2.begin(),
             n2_end = n2_iter + n;
        
        vector<int> res;
        res.reserve(n+m);
        
        while(n1_iter != n1_end && n2_iter != n2_end)
        if(*n1_iter <  *n2_iter)
        {
            res.push_back(*n1_iter);
            n1_iter++;
            if(n1_iter == n1_end)
                res.insert(end(res), n2_iter, n2_end);
        }
        else
        {
            res.push_back(*n2_iter);
            n2_iter++;
            if(n2_iter == n2_end)
                res.insert(end(res), n1_iter, n1_end);
        }
        
        nums1 = std::move(res);
    }
};
```
