# Range Extraction

## [Range Extraction](https://www.codewars.com/kata/51ba717bb08c1cd60f00002f)

A format for expressing an ordered list of integers is to use a comma separated list of either

* individual integers
* or a range of integers denoted by the starting integer separated from the end integer in the range by a dash, '-'. The range includes all integers in the interval including both endpoints.  It is not considered a range unless it spans at least 3 numbers. For example \("12, 13, 15-17"\)

Complete the solution so that it takes a list of integers in increasing order and returns a correctly formatted string in the range format.

**Example:**

```javascript
solution([-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20]);
// returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

```coffeescript
solution([-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20])
# returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

```ruby
solution([-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20])
# returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

```python
solution([-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20])
# returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

```java
Solution.rangeExtraction(new int[] {-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20})
# returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

```text
RangeExtraction.Extract(new[] {-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20});
# returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

```cpp
range_extraction({-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20});
// returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

```c
range_extraction((const []){-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20}, 20);
/* returns "-6,-3-1,3-5,7-11,14,15,17-20" */
```

```text
nums:  dd  -6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20

mov rdi, nums
mov rsi, 20
call range_extraction
; RAX <- `-6,-3-1,3-5,7-11,14,15,17-20\0`
```

```julia
rangeextraction([-6 -3 -2 -1 0 1 3 4 5 7 8 9 10 11 14 15 17 18 19 20])
# returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

```scala
solution(List(-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20))
// "-6,-3-1,3-5,7-11,14,15,17-20"
```

```text
(solution '(-6 -3 -2 -1 0 1 3 4 5 7 8 9 10 11 14 15 17 18 19 20))
; returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

_Courtesy of rosettacode.org_

## Solutions

### 🧠 C++

```cpp
#include <string>
#include <vector>
using std::to_string;

std::string range_extraction(std::vector<int> args)
{
  std::string res = to_string(args[0]);
  bool is_range = false;

  for (int i = 1, prev = args[0], range_len = 0;
       i < args.size(); prev = args[i++])
  {
    int fi = i == args.size()-1;
    if (args[i] == prev+1)
    {
      is_range = true;
      range_len++;
    }
    if (fi) //special logic for the last element
    {
     if (range_len > 1 && args[i] == prev+1)
        res+='-'+ to_string(args[i]);
      else if (range_len > 1) // but last element is not part of the seq
        res+='-'+ to_string(args[i-1])+','+to_string(args[i]);
      else if (range_len == 1 &&  args[i] != prev+1)
        res+=',' + to_string(args[i-1]) +','+to_string(args[i]);
      else
        res+=',' + to_string(args[i]);

      break;
    }
    else if(args[i] != prev+1) // non sequence logic
    {
      if(range_len) //we got here every time when sequence ends
      {
        if (range_len > 1)
          res+='-'+ to_string(args[i-1]);
        else if (range_len == 1)
          res+=',' + to_string(args[i-1]);

        range_len = 0;
        is_range = false;
      }
      res+=',' + to_string(args[i]);
    }

  }

  return res;
}
```

