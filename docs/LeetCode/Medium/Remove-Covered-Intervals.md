## [Remove Covered Intervals](https://leetcode.com/problems/remove-covered-intervals)

<p>Given a list of <code>intervals</code>, remove all intervals that are covered by another interval in the list.</p>

<p>Interval <code>[a,b)</code> is covered by&nbsp;interval <code>[c,d)</code> if and only if <code>c &lt;= a</code> and <code>b &lt;= d</code>.</p>

<p>After doing so, return <em>the number of remaining intervals</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[1,4],[3,6],[2,8]]
<strong>Output:</strong> 2
<b>Explanation: </b>Interval [3,6] is covered by [2,8], therefore it is removed.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[1,4],[2,3]]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[0,10],[5,12]]
<strong>Output:</strong> 2
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[3,10],[4,10],[5,11]]
<strong>Output:</strong> 2
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[1,2],[1,4],[3,4]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= intervals.length &lt;= 1000</code></li>
	<li><code>intervals[i].length == 2</code></li>
	<li><code>0 &lt;= intervals[i][0] &lt;&nbsp;intervals[i][1] &lt;= 10^5</code></li>
	<li>All the intervals are <strong>unique</strong>.</li>
</ul>

## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
    enum {START, END};

public:
    
    //O(n log n) solution: sort + 1 pass
    int removeCoveredIntervals(vector<vector<int>>& intervals)
    {
        std::sort(begin(intervals), end(intervals),
                 [](auto a, auto b)
                 {
                   return a[END] == b[END] ? a[START] > b[START] : a[END] < b[END];  
                 }
                 );
        
        //copy data to list for O(1) erasure
        std::list<vector<int>> i_vals(begin(intervals), end(intervals));

        
        //ENDs is already sorted, so next element has end >= than prev
        //only thing is to check the start of the interval, if prev has START > next start
        //then it's covered
        for(auto iter = begin(i_vals); iter != prev(end(i_vals));)
        {
            if((*iter)[START] >= (*next(iter))[START])
            {
                iter = i_vals.erase(iter);
                if(iter != begin(i_vals))
                    advance(iter, -1);
            }
            else
                ++iter;
        }
        
        return i_vals.size();
    }
};
```
