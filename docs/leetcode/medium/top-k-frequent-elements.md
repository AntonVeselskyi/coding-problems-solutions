# Top K Frequent Elements

## [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements)

Given a non-empty array of integers, return the **k** most frequent elements.

**Example 1:**

```text

Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2:**

```text

Input: nums = [1], k = 1
Output: [1]
```

**Note:**

* You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
* Your algorithm's time complexity **must be** better than O\(n log n\), where n is the array's size.
* It's guaranteed that the answer is unique, in other words the set of the top k frequent elements is unique.
* You can return the answer in any order.

## Solutions

### 🧠 Cpp

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

