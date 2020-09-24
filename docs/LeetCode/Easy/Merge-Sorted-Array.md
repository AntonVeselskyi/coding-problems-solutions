## [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array)

<p>Given two sorted integer arrays <em>nums1</em> and <em>nums2</em>, merge <em>nums2</em> into <em>nums1</em> as one sorted array.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>The number of elements initialized in <em>nums1</em> and <em>nums2</em> are <em>m</em> and <em>n</em> respectively.</li>
	<li>You may assume that <em>nums1</em> has enough space (size that is&nbsp;<strong>equal</strong> to <em>m</em> + <em>n</em>) to hold additional elements from <em>nums2</em>.</li>
</ul>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

<strong>Output:</strong>&nbsp;[1,2,2,3,5,6]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-10^9 &lt;= nums1[i], nums2[i] &lt;= 10^9</code></li>
	<li><code>nums1.length == m + n</code></li>
	<li><code>nums2.length == n</code></li>
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
