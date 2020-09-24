## [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array)

<p>Given an array of integers where 1 &le; a[i] &le; <i>n</i> (<i>n</i> = size of array), some elements appear twice and others appear once.</p>

<p>Find all the elements of [1, <i>n</i>] inclusive that do not appear in this array.</p>

<p>Could you do it without extra space and in O(<i>n</i>) runtime? You may assume the returned list does not count as extra space.</p>

<p><b>Example:</b>
<pre>
<b>Input:</b>
[4,3,2,7,8,2,3,1]

<b>Output:</b>
[5,6]
</pre>
</p>

## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    vector<int> findDisappearedNumbers(vector<int>& nums)
    {
        set<int> all_nums;
        for(int i = 1; i <= nums.size(); ++i)
            all_nums.insert(i);
        
        for(auto num : nums)
            all_nums.erase(num);
        
        return vector<int>(begin(all_nums),end(all_nums));    
    }
};
```
