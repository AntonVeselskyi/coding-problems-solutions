# Longest Substring Without Repeating Characters

## [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters)

Given a string `s`, find the length of the **longest substring** without repeating characters.

**Example 1:**

```text

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

**Example 2:**

```text

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```text

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Example 4:**

```text

Input: s = ""
Output: 0
```

**Constraints:**

* `0 <= s.length <= 5 * 104`
* `s` consists of English letters, digits, symbols and spaces.

## Solutions

### 🧠 Cpp

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s)
    {
        if(s.empty())
            return 0;

        int res = 0;
        string substr = "";
        for(char ch : s)
        {
            auto ch_in_res_indx = substr.find(ch);
            if(ch_in_res_indx == std::string::npos)
                substr.push_back(ch);
            else
            {
                if(substr.size() > res)
                    res = substr.size();
                substr.erase(substr.begin(), substr.begin()+ch_in_res_indx+1);
                substr.push_back(ch);
            }
        }

        if(substr.size() > res)
                    res = substr.size();
        return res;

    }
};
```

