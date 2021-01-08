## [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string)

<p>Given a string, find the first non-repeating character in it and return its index. If it doesn&#39;t exist, return -1.</p>

<p><b>Examples:</b></p>

<pre>
s = &quot;leetcode&quot;
return 0.

s = &quot;loveleetcode&quot;
return 2.
</pre>

<p>&nbsp;</p>

<p><b>Note:</b> You may assume the string contains only lowercase English letters.</p>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
public:
    int firstUniqChar(string s)
    {
//         map<char, int> counter;
        
//         for(char ch : s)
//             counter[ch]++;
        
//         for(size_t i = 0; i < s.size(); ++i)
//             if(counter[s[i]] == 1)
//                 return i;
        
        
        int first_bitmask = 0, second_bitmask = 0;
        for(char ch : s)
        {
            const uint8_t ch_pos = ch - 'a';
            if(! (first_bitmask & 1 << ch_pos) )
               first_bitmask |= 1 << ch_pos;
            else
               second_bitmask |= 1 << ch_pos;
        }
        
        for(int i = 0; i< s.size(); ++i)
            if(  
               !(second_bitmask & 1 << (s[i] - 'a')) 
               && first_bitmask & 1 << (s[i] - 'a')
              )
                    return i;

         return -1;        
    }
};
```
