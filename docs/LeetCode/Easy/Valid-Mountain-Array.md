## [Valid Mountain Array](https://leetcode.com/problems/valid-mountain-array)

<p>Given an array <code>A</code> of integers, return <code>true</code> if and only if it is a <em>valid mountain array</em>.</p>

<p>Recall that A is a mountain array if and only if:</p>

<ul>
	<li><code>A.length &gt;= 3</code></li>
	<li>There exists some <code>i</code> with&nbsp;<code>0 &lt; i&nbsp;&lt; A.length - 1</code>&nbsp;such that:
	<ul>
		<li><code>A[0] &lt; A[1] &lt; ... A[i-1] &lt; A[i] </code></li>
		<li><code>A[i] &gt; A[i+1] &gt; ... &gt; A[A.length - 1]</code></li>
	</ul>
	</li>
</ul>

<br>
<img src="https://assets.leetcode.com/uploads/2019/10/20/hint_valid_mountain_array.png" width="500" />

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[2,1]</span>
<strong>Output: </strong><span id="example-output-1">false</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[3,5,5]</span>
<strong>Output: </strong><span id="example-output-2">false</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">[0,3,2,1]</span>
<strong>Output: </strong><span id="example-output-3">true</span></pre>
</div>
</div>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>0 &lt;= A.length &lt;= 10000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 10000&nbsp;</code></li>
</ol>

<div>
<p>&nbsp;</p>

<div>
<div>&nbsp;</div>
</div>
</div>

## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    //O(n) solution
    bool validMountainArray(vector<int>& A)
    {
        //empty is no mountain
        if(A.empty())
            return false;

        bool going_up = true;
        for(auto iter = ++begin(A); iter < end(A); ++iter)
        {
            //no flat
            if(*iter == *prev(iter))
               return false;
            
            //go up
            if(*prev(iter) < *iter)
            {
                //if we went up after we went down
                if(!going_up)
                    return false;
            }
            //go down
            else if(*prev(iter) > *iter )
            {
                //if we going down from the start
                if(prev(iter) == begin(A))
                    return false;
                //started to gow down
                if(going_up)
                    going_up = false;
            }           
        }
        
        //if we were going up all the time, return false
        return !going_up;

    }
};
```
