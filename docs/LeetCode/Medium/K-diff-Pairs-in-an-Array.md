## [K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array)

<p>Given an array of integers <code>nums</code> and an integer <code>k</code>, return <em>the number of <b>unique</b> k-diff pairs in the array</em>.</p>

<p>A <b>k-diff</b> pair is&nbsp;an integer pair <code>(nums[i], nums[j])</code>, where the following are true:</p>

<ul>
	<li><code>0 &lt;= i, j &lt; nums.length</code></li>
	<li><code>i != j</code></li>
	<li><code>a &lt;= b</code></li>
	<li><code>b - a == k</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,1,4,1,5], k = 2
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are two 2-diff pairs in the array, (1, 3) and (3, 5).
Although we have two 1s in the input, we should only return the number of <strong>unique</strong> pairs.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5], k = 1
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are four 1-diff pairs in the array, (1, 2), (2, 3), (3, 4) and (4, 5).
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,1,5,4], k = 0
<strong>Output:</strong> 1
<strong>Explanation:</strong> There is one 0-diff pair in the array, (1, 1).
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,4,4,3,3,0,9,2,3], k = 3
<strong>Output:</strong> 2
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,-2,-3], k = 1
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>7</sup> &lt;= nums[i] &lt;= 10<sup>7</sup></code></li>
	<li><code>0 &lt;= k &lt;= 10<sup>7</sup></code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    int findPairs(vector<int>& nums, int k)
    {
        size_t count = 0;
        //O(n) solution, special case for k == 0
        if(k == 0)
        {
            //num, number of entries
            std::unordered_map<int, size_t> num_of_entries;
            for(int num : nums)
                num_of_entries[num]++;
            
            for(auto &entrie : num_of_entries)
                if(entrie.second > 1)
                    ++count;
            
            return count;
        }
        
        //O(n) solution for k > 0
        //for O(1) lookups if element is present, O(N) extra space
        std::unordered_set<int> lookup(begin(nums), end(nums));
        //iterate set to check only 'unique' pairs
        for(int num : lookup)
            if(lookup.find(num+k) != end(lookup))
                ++count;
        
        return count;
    }
};
```
