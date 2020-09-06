# Rotate Image

## [Rotate Image](https://leetcode.com/problems/rotate-image)

You are given an _n_ x _n_ 2D `matrix` representing an image, rotate the image by 90 degrees \(clockwise\).

You have to rotate the image [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm), which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

**Example 1:** ![](https://assets.leetcode.com/uploads/2020/08/28/mat1.jpg)

```text

Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]
```

**Example 2:** ![](https://assets.leetcode.com/uploads/2020/08/28/mat2.jpg)

```text

Input: matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
```

**Example 3:**

```text

Input: matrix = [[1]]
Output: [[1]]
```

**Example 4:**

```text

Input: matrix = [[1,2],[3,4]]
Output: [[3,1],[4,2]]
```

**Constraints:**

* `matrix.length == n`
* `matrix[i].length == n`
* `1 <= n <= 20`
* `-1000 <= matrix[i][j] <= 1000`

## Solutions

### 🧠 Cpp

```cpp
#include <cmath>
class Solution
{

/*
Approach:
rotate by layers
first X that Y
XXXX
XYYX
XYYX
XXXX
*/
public:
    void rotate(vector<vector<int>>& matrix)
    {
        int size = matrix.size();

        for(int i = 0; i < ceil(size/2.0); ++i)
            for(int j = i; j < (size-i*2)-1+i; ++j)
            {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[size-1-j][i];
                matrix[size-1-j][i] = matrix[size-1-i][size-1-j];
                matrix[size-1-i][size-1-j] = matrix[j][size-1-i];
                matrix[j][size-1-i] = temp;
            }
    }
};
```

