## [Insert Interval](https://leetcode.com/problems/insert-interval)

<p>Given a set of <em>non-overlapping</em> intervals, insert a new interval into the intervals (merge if necessary).</p>

<p>You may assume that the intervals were initially sorted according to their start times.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[1,3],[6,9]], newInterval = [2,5]
<strong>Output:</strong> [[1,5],[6,9]]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
<strong>Output:</strong> [[1,2],[3,10],[12,16]]
<strong>Explanation:</strong> Because the new interval <code>[4,8]</code> overlaps with <code>[3,5],[6,7],[8,10]</code>.</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> intervals = [], newInterval = [5,7]
<strong>Output:</strong> [[5,7]]
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[1,5]], newInterval = [2,3]
<strong>Output:</strong> [[1,5]]
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong> intervals = [[1,5]], newInterval = [2,7]
<strong>Output:</strong> [[1,7]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= intervals.length &lt;= 10<sup>4</sup></code></li>
	<li><code>intervals[i].length == 2</code></li>
	<li><code>0 &lt;=&nbsp;intervals[i][0] &lt;=&nbsp;intervals[i][1] &lt;= 10<sup>5</sup></code></li>
	<li><code>intervals</code>&nbsp;is sorted by <code>intervals[i][0]</code> in <strong>ascending</strong>&nbsp;order.</li>
	<li><code>newInterval.length == 2</code></li>
	<li><code>0 &lt;=&nbsp;newInterval[0] &lt;=&nbsp;newInterval[1] &lt;= 10<sup>5</sup></code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    vector<vector<int>> insert(vector<vector<int>>& intervals, vector<int>& newInterval)
    {
        //input check
        if(intervals.empty())
            return {newInterval};

        vector<vector<int>> res;
        res.reserve(intervals.size() + 1);
        int a = newInterval[0], b = newInterval[1]; 
        
        //find interval that could be altered to contain newInterval
        auto iter = begin(intervals),
                    iter_end = end(intervals);
        for(;iter < iter_end; ++iter)
        {
            int &x1 = iter->at(0), &x2 = iter->at(1);
            
            //booster to find correct element
            if(a > x1 && a > x2 && next(iter) != iter_end)
            {
                res.emplace_back(*iter);
                continue;
            }
            break;
        }
        
        //return {*iter};
        //alter this interval or insert new before interval it
        {
            int &x1 = iter->at(0), &x2 = iter->at(1);
            
            //(x1,a,b,x2) fully included
            if( x1 <= a && b <= x2 )
                return intervals;
            //(a,x1,x2,b) fully included
            if( a <= x1 && x2 <= b )
            {
                *iter = newInterval;
            }
            else if( a == x2 )
            {
                x2 = b;
            }
            //(a,x1,b,x2)
            else if( a < x1  && x1 <= b )
            {
                x1 = a;
            }
            //(x1,a,x2,b)
            else if( a <= x2 && x2 < b)
            {
                x2 = b;
            }
            //(a,b,x1,x2) //we can insert a new interval right before iter
            else if(x1 >= b)
            {
                iter = intervals.insert(iter, newInterval);//insert whole interval at prev pos
            }
            else if(next(iter) == iter_end)
            {
                if(a <= x2)
                    x2 = b;
                else
                {
                    res.emplace_back(*iter);
                    iter = intervals.insert(iter_end, newInterval);
                }
            }

        }

        //return {*iter};


        //check that intervals after modified/inserted one are not overlaping
        a = iter->at(0), b = iter->at(1);
        iter_end = end(intervals);
        auto finish_iter = next(iter);
        
        if(finish_iter != iter_end)
        for(;next(finish_iter) != iter_end; finish_iter++)
        {
            int &x1 = finish_iter->at(0), &x2 = finish_iter->at(1);
            if(b == x1 ||  b <= x2)
            {
                break;
            }
            if( b < next(finish_iter)->at(0))   
            {
                break;
            }
        }

        //take right valur from last overlapping
        if(finish_iter != iter_end)
        {
            int &x1 = finish_iter->at(0), &x2 = finish_iter->at(1);
            if(b >= x1)
            {
                if(x2 > b)
                    iter->at(1) = x2;
                finish_iter++;
            }
        }

        //at this point we finished with our interval,
        //all other intervals after it is not overlapping
        res.emplace_back(*iter);
        for(;finish_iter != iter_end; finish_iter++)
            res.emplace_back(*finish_iter);
        
        
        return res;
    }
};
```
