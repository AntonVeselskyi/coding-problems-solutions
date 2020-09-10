## [Valid Sudoku](https://leetcode.com/problems/valid-sudoku)

<p>Determine if a&nbsp;9x9 Sudoku board&nbsp;is valid.&nbsp;Only the filled cells need to be validated&nbsp;<strong>according to the following rules</strong>:</p>

<ol>
	<li>Each row&nbsp;must contain the&nbsp;digits&nbsp;<code>1-9</code> without repetition.</li>
	<li>Each column must contain the digits&nbsp;<code>1-9</code>&nbsp;without repetition.</li>
	<li>Each of the 9 <code>3x3</code> sub-boxes of the grid must contain the digits&nbsp;<code>1-9</code>&nbsp;without repetition.</li>
</ol>

<p><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png" style="height:250px; width:250px" /><br />
<small>A partially filled sudoku which is valid.</small></p>

<p>The Sudoku board could be partially filled, where empty cells are filled with the character <code>&#39;.&#39;</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong>
[
  [&quot;5&quot;,&quot;3&quot;,&quot;.&quot;,&quot;.&quot;,&quot;7&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],
  [&quot;6&quot;,&quot;.&quot;,&quot;.&quot;,&quot;1&quot;,&quot;9&quot;,&quot;5&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],
  [&quot;.&quot;,&quot;9&quot;,&quot;8&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;6&quot;,&quot;.&quot;],
  [&quot;8&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;6&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;3&quot;],
  [&quot;4&quot;,&quot;.&quot;,&quot;.&quot;,&quot;8&quot;,&quot;.&quot;,&quot;3&quot;,&quot;.&quot;,&quot;.&quot;,&quot;1&quot;],
  [&quot;7&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;2&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;6&quot;],
  [&quot;.&quot;,&quot;6&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;2&quot;,&quot;8&quot;,&quot;.&quot;],
  [&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;4&quot;,&quot;1&quot;,&quot;9&quot;,&quot;.&quot;,&quot;.&quot;,&quot;5&quot;],
  [&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;8&quot;,&quot;.&quot;,&quot;.&quot;,&quot;7&quot;,&quot;9&quot;]
]
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>
[
&nbsp; [&quot;8&quot;,&quot;3&quot;,&quot;.&quot;,&quot;.&quot;,&quot;7&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],
&nbsp; [&quot;6&quot;,&quot;.&quot;,&quot;.&quot;,&quot;1&quot;,&quot;9&quot;,&quot;5&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],
&nbsp; [&quot;.&quot;,&quot;9&quot;,&quot;8&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;6&quot;,&quot;.&quot;],
&nbsp; [&quot;8&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;6&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;3&quot;],
&nbsp; [&quot;4&quot;,&quot;.&quot;,&quot;.&quot;,&quot;8&quot;,&quot;.&quot;,&quot;3&quot;,&quot;.&quot;,&quot;.&quot;,&quot;1&quot;],
&nbsp; [&quot;7&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;2&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;6&quot;],
&nbsp; [&quot;.&quot;,&quot;6&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;2&quot;,&quot;8&quot;,&quot;.&quot;],
&nbsp; [&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;4&quot;,&quot;1&quot;,&quot;9&quot;,&quot;.&quot;,&quot;.&quot;,&quot;5&quot;],
&nbsp; [&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;8&quot;,&quot;.&quot;,&quot;.&quot;,&quot;7&quot;,&quot;9&quot;]
]
<strong>Output:</strong> false
<strong>Explanation:</strong> Same as Example 1, except with the <strong>5</strong> in the top left corner being 
    modified to <strong>8</strong>. Since there are two 8&#39;s in the top left 3x3 sub-box, it is invalid.
</pre>

<p><strong>Note:</strong></p>

<ul>
	<li>A Sudoku board (partially filled) could be valid but is not necessarily solvable.</li>
	<li>Only the filled cells need to be validated according to the mentioned&nbsp;rules.</li>
	<li>The given board&nbsp;contain only digits <code>1-9</code> and the character <code>&#39;.&#39;</code>.</li>
	<li>The given board size is always <code>9x9</code>.</li>
</ul>


## Solutions
#### 🧠 Cpp
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
