## [Count Negative Numbers in a Sorted Matrix](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix)

<p>Given a <code>m x n</code> matrix <code>grid</code> which is sorted in non-increasing order both row-wise and column-wise, return <em>the number of <strong>negative</strong> numbers in</em> <code>grid</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> grid = [[4,3,2,-1],[3,2,1,-1],[1,1,-1,-2],[-1,-1,-2,-3]]
<strong>Output:</strong> 8
<strong>Explanation:</strong> There are 8 negatives number in the matrix.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[3,2],[1,0]]
<strong>Output:</strong> 0
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1,-1],[-1,-1]]
<strong>Output:</strong> 3
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> grid = [[-1]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li><code>-100 &lt;= grid[i][j] &lt;= 100</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you find an <code>O(n + m)</code> solution?

## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    int countNegatives(vector<vector<int>>& grid)
    {
        const size_t m = grid.size(),
                     n = grid.front().size();
        
        int negative_num = 0;
        //m * log(n) solution, binary search in each row
        for(auto &row : grid)
        {
            int l = 0, r = n-1;
            int first_negative = -1;
            while(l <= r)
            {
                size_t mid = (l+r)/2;
                if(row[mid] < 0)
                {
                    first_negative = mid;
                    r = mid - 1;
                }
                else
                    l = mid + 1;
            }
            
            //if found negatives, count them (all nums after the index)
            if(first_negative != -1)
                negative_num += n - first_negative;
        }
        
        return negative_num;
    }
};
```
