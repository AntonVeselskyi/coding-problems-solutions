# Image Overlap

## [Image Overlap](https://leetcode.com/problems/image-overlap)

Two images `A` and `B` are given, represented as binary, square matrices of the same size.  \(A binary matrix has only 0s and 1s as values.\)

We translate one image however we choose \(sliding it left, right, up, or down any number of units\), and place it on top of the other image.  After, the _overlap_ of this translation is the number of positions that have a 1 in both images.

\(Note also that a translation does **not** include any kind of rotation.\)

What is the largest possible overlap?

**Example 1:**

```text

Input: A = [[1,1,0],
            [0,1,0],
            [0,1,0]]
       B = [[0,0,0],
            [0,1,1],
            [0,0,1]]
Output: 3
Explanation: We slide A to right by 1 unit and down by 1 unit.
```

**Notes:** 

1. `1 <= A.length = A[0].length = B.length = B[0].length <= 30`
2. `0 <= A[i][j], B[i][j] <= 1`

## Solutions

### 🧠 Cpp

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

