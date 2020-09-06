# Random Point in Non-overlapping Rectangles

## [Random Point in Non-overlapping Rectangles](https://leetcode.com/problems/random-point-in-non-overlapping-rectangles)

Given a list of **non-overlapping** axis-aligned rectangles `rects`, write a function `pick` which randomly and uniformily picks an **integer point** in the space covered by the rectangles.

Note:

1. An **integer point** is a point that has integer coordinates. 
2. A point on the perimeter of a rectangle is **included** in the space covered by the rectangles. 
3. `i`th rectangle = `rects[i]` = `[x1,y1,x2,y2]`, where `[x1, y1]` are the integer coordinates of the bottom-left corner, and `[x2, y2]` are the integer coordinates of the top-right corner.
4. length and width of each rectangle does not exceed `2000`.
5. `1 <= rects.length <= 100`
6. `pick` return a point as an array of integer coordinates `[p_x, p_y]`
7. `pick` is called at most `10000` times.

**Example 1:**

```text

Input: 
["Solution","pick","pick","pick"]
[[[[1,1,5,5]]],[],[],[]]
Output: 
[null,[4,1],[4,1],[3,3]]
```

**Example 2:**

```text

Input: 
["Solution","pick","pick","pick","pick","pick"]
[[[[-2,-2,-1,-1],[1,0,3,0]]],[],[],[],[],[]]
Output: 
[null,[-1,-2],[2,0],[-2,-1],[3,0],[-2,-2]]
```

**Explanation of Input Syntax:**

The input is two lists: the subroutines called and their arguments. `Solution`'s constructor has one argument, the array of rectangles `rects`. `pick` has no arguments. Arguments are always wrapped with a list, even if there aren't any.

## Solutions

### 🧠 Cpp

```cpp
#include <cstdlib>
#include <cmath>
#include <time.h>

class Solution
{
    struct rect_info
    {
        const size_t start, end;
        const int length, height;
        vector<int>& rect;
    };

    size_t total_num_of_points = 0;    
    vector<vector<int>>& _rects;
    vector<rect_info> _rect_infos;

public:
    Solution(vector<vector<int>>& rects) : _rects(rects)
    {
        srand(time(NULL));

        for(auto &rect : _rects)
        {
            const int
                length = abs(rect[2] - rect[0]), //x2 - x1 
                height = abs(rect[3] - rect[1]); //y2 - y1
            size_t rec_num_of_points = (length+1)*(height+1);

            _rect_infos.push_back({total_num_of_points, total_num_of_points + rec_num_of_points,
                                     length, height, rect});

            total_num_of_points += rec_num_of_points;
        }
    }

    vector<int> pick()
    {
        //select random rect
        size_t point_index = rand()%total_num_of_points;
        rect_info *ri = nullptr;
        for(auto &r_info : _rect_infos)
        {
            if(r_info.start <= point_index && point_index < r_info.end)   
            {
                ri = &r_info;
                break;
            }
        }

        //select random point 
       const int
            x_offset = ri->length ? rand()%(ri->length+1) : 0,
            y_offset = ri->height ? rand()%(ri->height+1) : 0;

        return { ri->rect[0] + x_offset, ri->rect[1] + y_offset};        
    }
};

/**
 * Your Solution object will be instantiated and called as such:
 * Solution* obj = new Solution(rects);
 * vector<int> param_1 = obj->pick();
 */
```

