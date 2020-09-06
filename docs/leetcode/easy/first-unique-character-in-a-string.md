# First Unique Character in a String

## [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string)

Given a string, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.

**Examples:**

```text

s = "leetcode"
return 0.

s = "loveleetcode"
return 2.
```

**Note:** You may assume the string contains only lowercase English letters.

## Solutions

### 🧠 Cpp

```cpp
#include <algorithm>

class Solution {
public:
    int firstUniqChar(string s)
    {
        int first_bitmask = 0, second_bitmask = 0;
        for(auto iter = s.begin(); iter != s.end(); ++iter)
        {
            if(! (first_bitmask & 1 << (*iter - 'a')) )
               first_bitmask |= 1 << *iter - 'a';
            else if(! (second_bitmask & 1 << (*iter - 'a')) )
               second_bitmask |= 1 << *iter - 'a';
        }

        for(int i = 0; i< s.size(); ++i)
            if( first_bitmask & 1 << (s[i] - 'a') 
               && !(second_bitmask & 1 << (s[i] - 'a')) )
                    return i;
        return -1;
    }
};
```

