## [Valid Mountain Array](https://leetcode.com/problems/valid-mountain-array)

<p>Given an array of integers <code>arr</code>, return <em><code>true</code> if and only if it is a valid mountain array</em>.</p>

<p>Recall that arr is a mountain array if and only if:</p>

<ul>
	<li><code>arr.length &gt;= 3</code></li>
	<li>There exists some <code>i</code> with <code>0 &lt; i &lt; arr.length - 1</code> such that:
	<ul>
		<li><code>arr[0] &lt; arr[1] &lt; ... &lt; arr[i - 1] &lt; arr[i] </code></li>
		<li><code>arr[i] &gt; arr[i + 1] &gt; ... &gt; arr[arr.length - 1]</code></li>
	</ul>
	</li>
</ul>
<img src="https://assets.leetcode.com/uploads/2019/10/20/hint_valid_mountain_array.png" width="500" />
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> arr = [2,1]
<strong>Output:</strong> false
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> arr = [3,5,5]
<strong>Output:</strong> false
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> arr = [0,3,2,1]
<strong>Output:</strong> true
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= arr[i] &lt;= 10<sup>4</sup></code></li>
</ul>


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
