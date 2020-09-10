## [Fizz Buzz](https://leetcode.com/problems/fizz-buzz)

<p>Write a program that outputs the string representation of numbers from 1 to <i>n</i>.</p>

<p>But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.</p>

<p><b>Example:</b>
<pre>
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
</pre>
</p>

## Solutions
#### 🧠 Cpp
```cpp
class Solution {
public:
    vector<string> fizzBuzz(int n)
    {
        vector<string> res;
        for(size_t i = 1; i<=n; ++i)
        {
            string fb = "";
            if(!(i%3))
                fb+="Fizz";
            if(!(i%5))
                fb+="Buzz";
            if(fb.empty())
                fb = std::to_string(i);
            
            res.push_back(fb);
        }
        
        return res;
    }
};
```
