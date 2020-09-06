# Transpose Matrix

## [Transpose Matrix](https://leetcode.com/problems/transpose-matrix)

Given a matrix `A`, return the transpose of `A`.

The transpose of a matrix is the matrix flipped over it's main diagonal, switching the row and column indices of the matrix.

![](https://assets.leetcode.com/uploads/2019/10/20/hint_transpose.png)

**Example 1:**

```text

Input: [[1,2,3],[4,5,6],[7,8,9]]
Output: [[1,4,7],[2,5,8],[3,6,9]]
```

**Example 2:**

```text

Input: [[1,2,3],[4,5,6]]
Output: [[1,4],[2,5],[3,6]]
```

**Note:**

1. `1 <= A.length <= 1000`
2. `1 <= A[0].length <= 1000`

## Solutions

### 🧠 Cpp

```cpp
class Solution
{
public:
    vector<vector<int>> transpose(vector<vector<int>>& A)
    {
        const size_t  new_length = A.size(),
                      new_height = A[0].size();
        vector<vector<int>> res;
        res.resize(new_height);
        for(auto &v : res)
            v.resize(new_length);

        for(size_t i = 0; i < new_length; ++i)
            for(size_t j = 0; j < new_height; ++j)
                res[j][i] = A[i][j];

        return res;
    }
};
```

