## [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix)

<p>Write a function to find the longest common prefix string amongst an array of strings.</p>

<p>If there is no common prefix, return an empty string <code>&quot;&quot;</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> strs = [&quot;flower&quot;,&quot;flow&quot;,&quot;flight&quot;]
<strong>Output:</strong> &quot;fl&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> strs = [&quot;dog&quot;,&quot;racecar&quot;,&quot;car&quot;]
<strong>Output:</strong> &quot;&quot;
<strong>Explanation:</strong> There is no common prefix among the input strings.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= strs.length &lt;= 200</code></li>
	<li><code>0 &lt;= strs[i].length &lt;= 200</code></li>
	<li><code>strs[i]</code> consists of only lower-case English letters.</li>
</ul>


## Solutions
#### 🧠 Cpp
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
