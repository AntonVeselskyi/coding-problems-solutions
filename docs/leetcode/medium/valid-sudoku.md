# Valid Sudoku

## [Valid Sudoku](https://leetcode.com/problems/valid-sudoku)

Determine if a 9x9 Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:

1. Each row must contain the digits `1-9` without repetition.
2. Each column must contain the digits `1-9` without repetition.
3. Each of the 9 `3x3` sub-boxes of the grid must contain the digits `1-9` without repetition.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)  
 A partially filled sudoku which is valid.

The Sudoku board could be partially filled, where empty cells are filled with the character `'.'`.

**Example 1:**

```text

Input:
[
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: true
```

**Example 2:**

```text

Input:
[
  ["8","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: false
Explanation: Same as Example 1, except with the 5 in the top left corner being 
    modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
```

**Note:**

* A Sudoku board \(partially filled\) could be valid but is not necessarily solvable.
* Only the filled cells need to be validated according to the mentioned rules.
* The given board contain only digits `1-9` and the character `'.'`.
* The given board size is always `9x9`.

## Solutions

### 🧠 Cpp

```cpp
#include <algorithm>
#include <map>


enum SudokuBitmap
{
    a1 = 1 << 1,
    a2 = 1 << 2,
    a3 = 1 << 3,
    a4 = 1 << 4,
    a5 = 1 << 5,
    a6 = 1 << 6,
    a7 = 1 << 7,
    a8 = 1 << 8,
    a9 = 1 << 9
};

map<char, SudokuBitmap> SudokuMap
{
{'1',a1},
{'2',a2},
{'3',a3},
{'4',a4},
{'5',a5},
{'6',a6},
{'7',a7},
{'8',a8},
{'9',a9}
};

class Solution
{
public:
    bool isValidSudoku(vector<vector<char>>& board)
    {
        short flags = 0;

        const auto cell_is_invalid =
            [&flags, SudokuMap](char a)
            {

                if( !(a == '.' || (a > '0' && a < '9'+1)) ) 
                    return true;
                if(flags & SudokuMap[a])
                    return true;

                flags |= SudokuMap[a];
                return false;
            };


        //check all rows   
        for(auto row : board)
        {
            flags = 0;
            bool invalid = count_if(row.begin(), row.end(), cell_is_invalid);
            if(invalid) return false;
        }

        //check all columns
        for(unsigned i = 0; i < board.size(); ++i)
        {
            flags = 0;
            for(unsigned j = 0; j < board.size(); ++j)
                if(cell_is_invalid(board[j][i]))
                    return false;
        }

        //check every 3x3
        for(unsigned i = 0; i < board.size(); i+=3)
            for(unsigned j = 0; j < board.size(); j+=3)
            {
                flags = 0;
                if(
                  cell_is_invalid(board[i][j]) ||
                  cell_is_invalid(board[i][j+1]) ||
                  cell_is_invalid(board[i][j+2]) ||
                  cell_is_invalid(board[i+1][j]) ||
                  cell_is_invalid(board[i+1][j+1]) ||
                  cell_is_invalid(board[i+1][j+2]) ||
                  cell_is_invalid(board[i+2][j]) ||
                  cell_is_invalid(board[i+2][j+1]) ||
                  cell_is_invalid(board[i+2][j+2])
                 ) return false;
            }

        return true;
    }
};
```

