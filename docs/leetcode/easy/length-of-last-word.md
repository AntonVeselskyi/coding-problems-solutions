# Length of Last Word

## [Length of Last Word](https://leetcode.com/problems/length-of-last-word)

Given a string s consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word \(last word means the last appearing word if we loop from left to right\) in the string.

If the last word does not exist, return 0.

**Note:** A word is defined as a **maximal substring** consisting of non-space characters only.

**Example:**

```text

Input: "Hello World"
Output: 5
```

## Solutions

### 🧠 Cpp

```cpp
class Solution {
public:
    int lengthOfLastWord(string s)
    {
        int counter = 0;
        auto riter = s.rbegin();
        for(; *riter == ' '; riter++);
        for(; *riter!=' ' && riter!=s.rend(); riter++, counter++);
        return counter;
    }
};
```

