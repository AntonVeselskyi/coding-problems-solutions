## [Palindrome Number](https://leetcode.com/problems/palindrome-number)

<p>Determine whether an integer is a palindrome. An integer&nbsp;is&nbsp;a&nbsp;palindrome when it&nbsp;reads the same backward as forward.</p>

<p><strong>Follow up:</strong> Could you solve&nbsp;it without converting the integer to a string?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> x = 121
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> x = -121
<strong>Output:</strong> false
<strong>Explanation:</strong> From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> x = 10
<strong>Output:</strong> false
<strong>Explanation:</strong> Reads 01 from right to left. Therefore it is not a palindrome.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> x = -101
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup>&nbsp;&lt;= x &lt;= 2<sup>31</sup>&nbsp;- 1</code></li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    bool isPalindrome(int x)
    {
        //negative is not palindrome
        if(x < 0)
            return false;
        if(x == 0)
            return true;
        //if last number is 0 it is not a polindrome
        if(x%10 == 0)
            return false;

        //O(1) space
        long reversed = 0;
             
        for(long mod = 10, div = 1;
            reversed < x;
            mod *= 10, div *= 10)
        {
            //put last character as first on reversed, and so on
            reversed = reversed*10 + (x%mod)/div;
        }
        
        return reversed == x;

        //STRING SOLUTION O(N) space
        /*
        string num = std::to_string(x);
        const size_t num_len = num.size();
        for(size_t i = 0; i < num_len/2; ++i)
            if(num[i] != num[num_len-1-i])
                return false;        
        return true;
        */
    }
};
```
