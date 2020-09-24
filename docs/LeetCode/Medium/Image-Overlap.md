## [Image Overlap](https://leetcode.com/problems/image-overlap)

<p>You are given two images <code>img1</code> and <code>img2</code>&nbsp;both of size <code>n x n</code>, represented as&nbsp;binary, square matrices of the same size. (A binary matrix has only 0s and 1s as values.)</p>

<p>We translate one image however we choose (sliding it left, right, up, or down any number of units), and place it on top of the other image.&nbsp; After, the <em>overlap</em> of this translation is the number of positions that have a 1 in both images.</p>

<p>(Note also that a translation does <strong>not</strong> include any kind of rotation.)</p>

<p>What is the largest possible overlap?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/09/overlap1.jpg" style="width: 450px; height: 231px;" />
<pre>
<strong>Input:</strong> img1 = [[1,1,0],[0,1,0],[0,1,0]], img2 = [[0,0,0],[0,1,1],[0,0,1]]
<strong>Output:</strong> 3
<strong>Explanation:</strong> We slide img1 to right by 1 unit and down by 1 unit.
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/09/overlap_step1.jpg" style="width: 450px; height: 105px;" />
The number of positions that have a 1 in both images is 3. (Shown in red)
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/09/overlap_step2.jpg" style="width: 450px; height: 231px;" />
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> img1 = [[1]], img2 = [[1]]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> img1 = [[0]], img2 = [[0]]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == img1.length</code></li>
	<li><code>n == img1[i].length</code></li>
	<li><code>n == img2.length </code></li>
	<li><code>n == img2[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 30</code></li>
	<li><code>img1[i][j]</code> is <code>0</code> or <code>1</code>.</li>
	<li><code>img2[i][j]</code> is <code>0</code> or <code>1</code>.</li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    int largestOverlap(vector<vector<int>>& A, vector<vector<int>>& B)
    {
        const size_t length = A.size();
        if(length == 1)
            return A[0][0] & B[0][0];
        
        size_t max_overlap_count = 0;
        
        for (int bi_offset = 0; bi_offset < length; ++bi_offset)
        for (int bj_offset = 0; bj_offset < length; ++bj_offset)
        {
            size_t overlap_count_a = 0,
                   overlap_count_b = 0;

            for (int i_a = 0, i_b = 0+bi_offset; i_b < length; ++i_a, ++i_b)
                for (int j_a = 0, j_b = 0+bj_offset; j_b < length; ++j_a, ++j_b)
                {
                    if(A[i_a][j_a] & B[i_b][j_b]) //move B over A
                        overlap_count_b++;
                    if(A[i_b][j_b] & B[i_a][j_a]) //move A over B
                        overlap_count_a++;
                }
            
            const size_t iteration_max = std::max(overlap_count_a, overlap_count_b);
            if(iteration_max > max_overlap_count)
                max_overlap_count = iteration_max;
        }

        return max_overlap_count;
    }
};
```
