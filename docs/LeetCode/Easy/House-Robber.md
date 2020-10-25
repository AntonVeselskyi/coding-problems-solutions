## [House Robber](https://leetcode.com/problems/house-robber)

<p>You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and <b>it will automatically contact the police if two adjacent houses were broken into on the same night</b>.</p>

<p>Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight <b>without alerting the police</b>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,1]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Rob house 1 (money = 1) and then rob house 3 (money = 3).
&nbsp;            Total amount you can rob = 1 + 3 = 4.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,7,9,3,1]
<strong>Output:</strong> 12
<strong>Explanation:</strong> Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
&nbsp;            Total amount you can rob = 2 + 9 + 1 = 12.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 100</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 400</code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{    
    //DP storage for function results
    map<vector<int>, int> cache;
    
public:    
    int rob(vector<int> money)
    {
        if(money.empty())
            return 0;
        
        //DP check cache
        auto found = cache.find(money);
        if(found != end(cache))
        {
            return found->second;
        }
        
        //if we can skip
        bool has_next_house = next(begin(money)) != end(money);
        
        //robbing the first house and skipping the next one (next(begin(money),2)
        int robbing_first_house_scenario =  
            money.front() + (has_next_house ? rob(vector<int>(next(begin(money),2), end(money))) : 0 );
        //second scenario is we skipping the current house and go right to the next one
        int skipping_first_house_scenario = rob(vector<int>(next(begin(money)), end(money)));
        
        int res = max(robbing_first_house_scenario, skipping_first_house_scenario);

        //DP add to cache
        cache.insert(make_pair(money, res));
        return res;
    }
};
```
