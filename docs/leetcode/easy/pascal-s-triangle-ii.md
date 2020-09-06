# Pascal's Triangle II

## [Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii)

Given an integer `rowIndex`, return the `rowIndexth` row of the Pascal's triangle.

Notice that the row index starts from **0**.

![](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)  
 In Pascal's triangle, each number is the sum of the two numbers directly above it.

**Follow up:**

Could you optimize your algorithm to use only _O_\(_k_\) extra space?

**Example 1:**

```text
Input: rowIndex = 3
Output: [1,3,3,1]
```

**Example 2:**

```text
Input: rowIndex = 0
Output: [1]
```

**Example 3:**

```text
Input: rowIndex = 1
Output: [1,1]
```

**Constraints:**

* `0 <= rowIndex <= 40`

## Solutions

### 🧠 Cpp

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

