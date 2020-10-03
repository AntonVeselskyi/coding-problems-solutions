## [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi)

<p>Implement <code><span>atoi</span></code> which&nbsp;converts a string to an integer.</p>

<p>The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.</p>

<p>The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.</p>

<p>If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.</p>

<p>If no valid conversion could be performed, a zero value is returned.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>Only the space character <code>&#39; &#39;</code> is considered a whitespace character.</li>
	<li>Assume we are dealing with an environment that could only store integers within the 32-bit signed integer range: [&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1]. If the numerical value is out of the range of representable values, INT_MAX (2<sup>31&nbsp;</sup>&minus; 1) or INT_MIN (&minus;2<sup>31</sup>) is returned.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> str = &quot;42&quot;
<strong>Output:</strong> 42
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> str = &quot;   -42&quot;
<strong>Output:</strong> -42
<strong>Explanation:</strong> The first non-whitespace character is &#39;-&#39;, which is the minus sign. Then take as many numerical digits as possible, which gets 42.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> str = &quot;4193 with words&quot;
<strong>Output:</strong> 4193
<strong>Explanation:</strong> Conversion stops at digit &#39;3&#39; as the next character is not a numerical digit.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> str = &quot;words and 987&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> The first non-whitespace character is &#39;w&#39;, which is not a numerical digit or a +/- sign. Therefore no valid conversion could be performed.
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong> str = &quot;-91283472332&quot;
<strong>Output:</strong> -2147483648
<strong>Explanation:</strong> The number &quot;-91283472332&quot; is out of the range of a 32-bit signed integer. Thefore INT_MIN (&minus;2<sup>31</sup>) is returned.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 200</code></li>
	<li><code>s</code> consists of English letters (lower-case and upper-case), digits, <code>&#39; &#39;</code>, <code>&#39;+&#39;</code>, <code>&#39;-&#39;</code> and <code>&#39;.&#39;</code>.</li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
#include <cmath>
#include <climits>

class Solution
{
public:
    int myAtoi(string str)
    {
        //check params
        if(str.empty())
            return 0;

        //get start position
        int start_pos = 0;
        bool number_started = false;
        for(;str[start_pos] == ' ' && !number_started || str[start_pos] == '0' ; start_pos++)
            if(str[start_pos] == '0') number_started = true;
        
        
        
        //validate it
        bool is_negative = false, is_signed = false;
        if(str[start_pos] == '-')
        {
            is_negative = true;
            is_signed = true;
        }
        else if(str[start_pos] == '+')
        {
            is_signed = true;
        }
        
        //no zeroes before sign
        if(is_signed)
        {   
            if(start_pos!=0 && str[start_pos-1] == '0')
                return 0;
            //skip sign for compounting
            start_pos++;
        }   
        
        //remove potential zeros after sign
        for(;str[start_pos] == '0' ; start_pos++);

        if(str[start_pos] < '0' || str[start_pos] > '9')
           return 0;
        
        
        //find end
        int delim_position=start_pos;
        while(str[++delim_position] >= '0' && str[delim_position] <= '9');
        
        //check for limits
        if( (delim_position - start_pos) > 10)
            return is_negative ? INT_MIN : INT_MAX;
        
        //case for near limit numbers
        if( (delim_position - start_pos) == 10)
        {
            string shorter_input(str.begin()+start_pos, str.begin()+delim_position-1);
            int shorter_input_value = myAtoi(shorter_input);
            if ( shorter_input_value > 214748364 
                || (shorter_input_value == 214748364 && str[delim_position-1] > '7') )
                return is_negative ? INT_MIN : INT_MAX;
        }
        
        //compound the result
        int result = 0;
        for(; start_pos < delim_position; ++start_pos)
            result += std::pow(10, delim_position - start_pos - 1) 
                      * (str[start_pos] - '0');
        
        if(is_negative)
            result*=-1;
        
        return result;
            
    }
};
```
