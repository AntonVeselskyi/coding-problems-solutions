## [Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii)

<p>Given an integer <code>rowIndex</code>, return the <code>rowIndex<sup>th</sup></code>&nbsp;row of the Pascal&#39;s triangle.</p>

<p>Notice&nbsp;that the row index starts from&nbsp;<strong>0</strong>.</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" /><br />
<small>In Pascal&#39;s triangle, each number is the sum of the two numbers directly above it.</small></p>

<p><strong>Follow up:</strong></p>

<p>Could you optimize your algorithm to use only <em>O</em>(<em>k</em>) extra space?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> rowIndex = 3
<strong>Output:</strong> [1,3,3,1]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> rowIndex = 0
<strong>Output:</strong> [1]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> rowIndex = 1
<strong>Output:</strong> [1,1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;=&nbsp;rowIndex &lt;= 40</code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    vector<int> getRow(int rowIndex)
    {
        vector<int> line = {1};
        
        while(rowIndex--)
        {
            vector<int> new_line;
            new_line.reserve(line.size()+1);
            
            new_line.emplace_back(1);
            if(line.size()!=1)
            {
                for(int i = 0; i <line.size()-1; ++i)
                    new_line.emplace_back(line[i]+line[i+1]);
            }
            new_line.emplace_back(1);
            
            line = std::move(new_line);
        }
        
        return line;
        
    }
};
```
