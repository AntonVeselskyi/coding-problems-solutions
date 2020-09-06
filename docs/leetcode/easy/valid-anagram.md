# Valid Anagram

## [Valid Anagram](https://leetcode.com/problems/valid-anagram)

Given two strings _s_ and _t_ , write a function to determine if _t_ is an anagram of _s_.

**Example 1:**

```text

Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**

```text

Input: s = "rat", t = "car"
Output: false
```

**Note:**  
 You may assume the string contains only lowercase alphabets.

**Follow up:**  
 What if the inputs contain unicode characters? How would you adapt your solution to such case?

## Solutions

### 🧠 Cpp

```cpp
#include <algorithm>
class Solution
{
public:
    bool isAnagram(string s, string t)
    {
        std::sort(s.begin(), s.end());
        std::sort(t.begin(), t.end());
        return s == t;
    }
};
```

