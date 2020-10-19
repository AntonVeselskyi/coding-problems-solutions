## [Climbing Stairs](https://leetcode.com/problems/climbing-stairs)

<p>You are climbing a stair case. It takes <em>n</em> steps to reach to the top.</p>

<p>Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 2
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 45</code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
    //max stairs num is 45
    array<int, 46> _storage = {0,1,2};
public:
    int climbStairs(int n)
    {
        if(!_storage[n])
            _storage[n] = climbStairs(n-1) + climbStairs(n-2);
        
        return _storage[n];
    }
};
```