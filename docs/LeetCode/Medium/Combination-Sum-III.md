## [Combination Sum III](https://leetcode.com/problems/combination-sum-iii)

<p>Find all valid combinations of <code>k</code> numbers that sum up to <code>n</code> such that the following conditions are true:</p>

<ul>
	<li>Only numbers <code>1</code> through <code>9</code> are used.</li>
	<li>Each number is used <strong>at most once</strong>.</li>
</ul>

<p>Return <em>a list of all possible valid combinations</em>. The list must not contain the same combination twice, and the combinations may be returned in any order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> k = 3, n = 7
<strong>Output:</strong> [[1,2,4]]
<strong>Explanation:</strong>
1 + 2 + 4 = 7
There are no other valid combinations.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> k = 3, n = 9
<strong>Output:</strong> [[1,2,6],[1,3,5],[2,3,4]]
<strong>Explanation:</strong>
1 + 2 + 6 = 9
1 + 3 + 5 = 9
2 + 3 + 4 = 9
There are no other valid combinations.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> k = 4, n = 1
<strong>Output:</strong> []
<strong>Explanation:</strong> There are no valid combinations. [1,2,1] is not valid because 1 is used twice.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> k = 3, n = 2
<strong>Output:</strong> []
<strong>Explanation:</strong> There are no valid combinations.
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong> k = 9, n = 45
<strong>Output:</strong> [[1,2,3,4,5,6,7,8,9]]
<strong>Explanation:</strong>
1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 = 45
​​​​​​​There are no other valid combinations.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= k &lt;= 9</code></li>
	<li><code>1 &lt;= n &lt;= 60</code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
    
    //size_t pick_next_free_position(char &bitmask, current)
public:
    vector<vector<int>> combinationSum3(int k, int n)
    {
        //input validation
        if(k > n)
            return {};
        
        vector<vector<int>> res;
        set<vector<int>> res_set;
        vector<int> holder(k, 1);
        //to mark current selected numbers
        
        size_t iter_max = std::min(9, (n > 3 ? n-k+1 : n));

        function<void(size_t, vector<int>)> increment_holder;
        //add vector of num to ignore to ignore
        increment_holder = [&](size_t pos, vector<int> to_ignore)
        {
            for(int i = 0; i <= iter_max; )
            {
                if(i == iter_max)
                {
                    holder[pos] = 1;
                    break;
                }

                if(pos==k-1)
                {
                    const int sum = std::accumulate(holder.begin(), holder.end(),0);
                    if(sum == n)
                    {
                        auto holder_copy = holder;
                        std::sort(holder_copy.begin(), holder_copy.end());
                        auto uq_end = std::unique(begin(holder_copy), end(holder_copy));
                        if(uq_end == end(holder_copy))
                            res_set.insert(std::move(holder_copy));
                    }
                    if(sum > n)
                    {
                        holder[pos] = 1;
                        break;
                    }
                }
                else
                {
                    to_ignore.push_back(holder[pos]);
                    increment_holder(pos+1, to_ignore);
                }
                do
                {
                    ++i, ++holder[pos];
                } while(std::count(begin(to_ignore), end(to_ignore),holder[pos]));
                
                if(i == iter_max)
                {
                    holder[pos] = 1;
                    break;
                }
                
                     
            }
        };
        
        increment_holder(0, {});

        std::copy(res_set.begin(), res_set.end(), back_inserter(res));
        
        return res;
    }
};
```
