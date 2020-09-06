# Longest Common Prefix

## [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix)

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**Example 1:**

```text

Input: ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**

```text

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Note:**

All given inputs are in lowercase letters `a-z`.

## Solutions

### 🧠 Cpp

```cpp
class Solution
{
public:
    string longestCommonPrefix(vector<string>& strs)
    {
        if(strs.empty())
            return "";

        string res = "";  
        bool keep_going = true;
        size_t first_str_size = strs[0].size(); 
        for(size_t i = 0; keep_going && i < first_str_size; i++)
        {
            char ch = strs[0][i];

            for(auto &str : strs)
                if(str.size() <= i || str[i] != ch)
                    keep_going = false;

            if(keep_going)
                res+=ch;      
        }

        return res;
    }
};
```

