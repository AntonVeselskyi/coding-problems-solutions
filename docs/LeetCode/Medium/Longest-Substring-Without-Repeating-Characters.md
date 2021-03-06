## [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters)

<p>Given a string <code>s</code>, find the length of the <b>longest substring</b> without repeating characters.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcabcbb&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> The answer is &quot;abc&quot;, with the length of 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bbbbb&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> The answer is &quot;b&quot;, with the length of 1.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;pwwkew&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> The answer is &quot;wke&quot;, with the length of 3.
Notice that the answer must be a substring, &quot;pwke&quot; is a subsequence and not a substring.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;&quot;
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> consists of English letters, digits, symbols and spaces.</li>
</ul>


## Solutions
#### 🧠 Cpp
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
