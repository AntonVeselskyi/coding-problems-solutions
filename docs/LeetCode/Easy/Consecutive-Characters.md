## [Consecutive Characters](https://leetcode.com/problems/consecutive-characters)

<p>Given a string <code>s</code>, the power of the string is the maximum length of a non-empty substring that&nbsp;contains only one unique character.</p>

<p>Return <em>the power</em>&nbsp;of the string.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcode&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> The substring &quot;ee&quot; is of length 2 with the character &#39;e&#39; only.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abbcccddddeeeeedcba&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The substring &quot;eeeee&quot; is of length 5 with the character &#39;e&#39; only.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;triplepillooooow&quot;
<strong>Output:</strong> 5
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;hooraaaaaaaaaaay&quot;
<strong>Output:</strong> 11
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;tourist&quot;
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 500</code></li>
	<li><code>s</code> contains only lowercase English letters.</li>
</ul>

## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    int maxPower(string s)
    {
        int max_power = 1, counter = 0;
        char prev = 0;
        auto update_max_flush_counter = [&](char ch)
        {
            max_power = std::max(max_power, counter);
            prev = ch;
            counter = 1;
        };
        
        for(char ch : s)
        {
            if(ch == prev)
                counter++;
            else
                update_max_flush_counter(ch);
        }
        update_max_flush_counter(s.back());
        
        return max_power;
    }
};
```
