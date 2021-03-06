## [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements)

<p>Given a non-empty array of integers, return the <b><i>k</i></b> most frequent elements.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>nums = <span id="example-input-1-1">[1,1,1,2,2,3]</span>, k = <span id="example-input-1-2">2</span>
<strong>Output: </strong><span id="example-output-1">[1,2]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>nums = <span id="example-input-2-1">[1]</span>, k = <span id="example-input-2-2">1</span>
<strong>Output: </strong><span id="example-output-2">[1]</span></pre>
</div>

<p><b>Note: </b></p>

<ul>
	<li>You may assume <i>k</i> is always valid, 1 &le; <i>k</i> &le; number of unique elements.</li>
	<li>Your algorithm&#39;s time complexity <b>must be</b> better than O(<i>n</i> log <i>n</i>), where <i>n</i> is the array&#39;s size.</li>
	<li>It&#39;s guaranteed that the answer is unique, in other words the set of the top k frequent elements is unique.</li>
	<li>You can return the answer in any order.</li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
#include <map>

class Solution
{
public:
    vector<int> topKFrequent(vector<int>& nums, int k)
    {
        std::map<int, int> input_map;
        for(int i : nums)
            input_map[i]++;
        
        //sort by values(freqency)
        std::multimap<int, int> sorted_input_map;
        for(auto p : input_map)
            sorted_input_map.insert({p.second, p.first});
        
        vector<int> res;
        for(auto iter = --sorted_input_map.end(); k--; --iter)
            res.push_back(iter->second);

        return res;
    }
};
```
