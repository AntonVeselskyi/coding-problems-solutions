# String to Integer \(atoi\)

## [String to Integer \(atoi\)](https://leetcode.com/problems/string-to-integer-atoi)

Implement `atoi` which converts a string to an integer.

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned.

**Note:**

* Only the space character `' '` is considered as whitespace character.
* Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: \[−231,  231 − 1\]. If the numerical value is out of the range of representable values, INT\_MAX \(231 − 1\) or INT\_MIN \(−231\) is returned.

**Example 1:**

```text

Input: "42"
Output: 42
```

**Example 2:**

```text

Input: "   -42"
Output: -42
Explanation: The first non-whitespace character is '-', which is the minus sign.
             Then take as many numerical digits as possible, which gets 42.
```

**Example 3:**

```text

Input: "4193 with words"
Output: 4193
Explanation: Conversion stops at digit '3' as the next character is not a numerical digit.
```

**Example 4:**

```text

Input: "words and 987"
Output: 0
Explanation: The first non-whitespace character is 'w', which is not a numerical 
             digit or a +/- sign. Therefore no valid conversion could be performed.
```

**Example 5:**

```text

Input: "-91283472332"
Output: -2147483648
Explanation: The number "-91283472332" is out of the range of a 32-bit signed integer.
             Thefore INT_MIN (−231) is returned.
```

## Solutions

### 🧠 Cpp

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

