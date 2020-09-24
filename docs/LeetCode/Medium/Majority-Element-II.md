## [Majority Element II](https://leetcode.com/problems/majority-element-ii)

<p>Given an integer array of size <i>n</i>, find all elements that appear more than <code>&lfloor; n/3 &rfloor;</code> times.</p>

<p><strong>Note: </strong>The algorithm should run in linear time and in O(1) space.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [3,2,3]
<strong>Output:</strong> [3]</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [1,1,1,3,3,2,2,2]
<strong>Output:</strong> [1,2]</pre>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    vector<int> majorityElement(vector<int>& nums)
    {
        std::map<int, size_t> marks;
        
        for(auto &num : nums)
            marks[num]++;
        
        const int limit = nums.size() / 3;
        vector<int> res;
        
        for(auto &mark : marks)
            if(mark.second > limit)
                res.push_back(mark.first);
        
        return res;
    }
};
```
