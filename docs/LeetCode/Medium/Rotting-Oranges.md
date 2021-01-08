## [Rotting Oranges](https://leetcode.com/problems/rotting-oranges)

<p>You are given an <code>m x n</code> <code>grid</code> where each cell can have one of three values:</p>

<ul>
	<li><code>0</code> representing an empty cell,</li>
	<li><code>1</code> representing a fresh orange, or</li>
	<li><code>2</code> representing a rotten orange.</li>
</ul>

<p>Every minute, any fresh orange that is <strong>4-directionally adjacent</strong> to a rotten orange becomes rotten.</p>

<p>Return <em>the minimum number of minutes that must elapse until no cell has a fresh orange</em>. If <em>this is impossible, return</em> <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/02/16/oranges.png" style="width: 650px; height: 137px;" />
<pre>
<strong>Input:</strong> grid = [[2,1,1],[1,1,0],[0,1,1]]
<strong>Output:</strong> 4
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[2,1,1],[0,1,1],[1,0,1]]
<strong>Output:</strong> -1
<strong>Explanation:</strong> The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> grid = [[0,2]]
<strong>Output:</strong> 0
<strong>Explanation:</strong> Since there are already no fresh oranges at minute 0, the answer is just 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10</code></li>
	<li><code>grid[i][j]</code> is <code>0</code>, <code>1</code>, or <code>2</code>.</li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{    
enum state{empty, fresh, rotten};
public:
    template<state state_to_check>
    bool is_cell(int i, int j, vector<vector<int>>& grid)
    {
        try
        {
            return grid.at(i).at(j) == state_to_check;
        }
        catch(const std::out_of_range)
        {
            return true;
        }
    }
    
    bool check_siders_is_present(int i, int j, vector<vector<int>>& g)
    {
        bool is_present = is_cell<empty>(i,j,g) || is_cell<rotten>(i,j,g) ? true :
           !(is_cell<empty>(i+1,j,g) && is_cell<empty>(i-1,j,g) 
             && is_cell<empty>(i,j+1,g) && is_cell<empty>(i,j-1,g));
        return is_present;
    }
    
    int orangesRotting(vector<vector<int>>& g)
    {
        //input check
        //if(g.size() == 1 && g[0].size() ==1 )
          //  return g[0][0] == rotten ? 0 : -1;
        
        //there is no cut off oranges
        for(int i = 0; i < g.size(); i++)
        for(int j = 0; j < g[i].size(); j++)
            if(check_siders_is_present(i,j,g) == false)
                return -1;
        
        //there is at least one rotten
        bool rotten_is_present = false,
             fresh_is_present = false;
        for(auto line : g)
        {
            if(count(line.begin(), line.end(), rotten))
            {
                rotten_is_present = true;
            }
            if(count(line.begin(), line.end(), fresh))
            {
                fresh_is_present = true;
            }
        }
        if(!rotten_is_present)
            return fresh_is_present ? -1 : 0;
        
        //start iteration
        vector<vector<int>> grid(g);
        queue<pair<int,int>> to_rot;
        bool all_rotten = false;
        size_t minutes = 0;
        
        auto rot_if_fresh = [&grid, &all_rotten](int i, int j)
        {
            try
            {
                if (grid.at(i).at(j) == fresh)
                {
                    grid[i][j] = rotten;
                    all_rotten = false;
                }
            }
            catch(const std::out_of_range){}
        };
        
        while(!all_rotten)
        {
            all_rotten = true; 
            for(int i = 0; i < grid.size(); i++)
            for(int j = 0; j < grid[i].size(); j++)
            {
                if(grid[i][j] == rotten)
                    to_rot.push({i,j});
            }
            
            while(!to_rot.empty()) 
            {
                auto p = to_rot.front(); to_rot.pop();
                
                int i = p.first, j = p.second;
                rot_if_fresh(i+1,j);
                rot_if_fresh(i-1,j);
                rot_if_fresh(i,j+1);
                rot_if_fresh(i,j-1);
            }
            
            if(!all_rotten)
                minutes++;
            
        }
        
        fresh_is_present = false;
        for(auto line : grid)
        if(count(line.begin(), line.end(), fresh))
        {
            fresh_is_present = true;
        }
        return fresh_is_present ? -1 : minutes;

    }
};
```
