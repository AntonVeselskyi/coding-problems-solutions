## [Minimum Domino Rotations For Equal Row](https://leetcode.com/problems/minimum-domino-rotations-for-equal-row)

<p>In a row of dominoes, <code>A[i]</code> and <code>B[i]</code> represent the top and bottom halves of the <code>i<sup>th</sup></code> domino.&nbsp; (A domino is a tile with two numbers from 1 to 6 - one on each half of the tile.)</p>

<p>We may rotate the <code>i<sup>th</sup></code> domino, so that <code>A[i]</code> and <code>B[i]</code> swap values.</p>

<p>Return the minimum number of rotations so that all the values in <code>A</code> are the same, or all the values in <code>B</code>&nbsp;are the same.</p>

<p>If it cannot be done, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/03/08/domino.png" style="height: 161px; width: 200px;" />
<pre>
<strong>Input:</strong> A = [2,1,2,4,2,2], B = [5,2,6,2,3,2]
<strong>Output:</strong> 2
<strong>Explanation:</strong> 
The first figure represents the dominoes as given by A and B: before we do any rotations.
If we rotate the second and fourth dominoes, we can make every value in the top row equal to 2, as indicated by the second figure.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> A = [3,5,1,2,3], B = [3,6,3,3,4]
<strong>Output:</strong> -1
<strong>Explanation:</strong> 
In this case, it is not possible to rotate the dominoes to make one row of values equal.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= A.length == B.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= A[i], B[i] &lt;= 6</code></li>
</ul>


## Solutions
#### 🐍 Python
```python
class Solution:
    def minDominoRotations(self, A: List[int], B: List[int]) -> int:
        cA, cB = Counter(A).most_common(), Counter(B).most_common()
        
        #find most frequent on top and bottom
        top_frequent, bottom_frequent = [cA[0][0]], [cB[0][0]]
        
        #if there more then one element with top count, add them
        top_frequent.extend([ch for ch,i in cA[1:] if i == cA[0][0]])
        bottom_frequent.extend([ch for ch,i in cB[1:] if i == cB[0][0]])
        
        #find min rotation (try top then bottom)
        min_count = -1
        for ch in top_frequent:
            local_counter = 0
            for i, domino_ch in enumerate(A):
                if domino_ch == ch:
                    continue
                elif B[i] == ch:
                    local_counter+=1
                    continue
                else:
                    break
            else:
                if min_count == -1 or local_counter < min_count:
                    min_count = local_counter
                    
        for ch in bottom_frequent:
            local_counter = 0
            for i, domino_ch in enumerate(B):
                if domino_ch == ch:
                    continue
                elif A[i] == ch:
                    local_counter+=1
                    continue
                else:
                    break
            else:
                if min_count == -1 or local_counter < min_count:
                    min_count = local_counter
        
        return min_count
                    
        
```
