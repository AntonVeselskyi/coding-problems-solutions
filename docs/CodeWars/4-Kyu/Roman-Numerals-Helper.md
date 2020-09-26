## [Roman Numerals Helper](https://www.codewars.com/kata/51b66044bce5799a7f000003)

## Task

Create a RomanNumerals class that can convert a roman numeral to and from an integer value.  It should follow the API demonstrated in the examples below. Multiple roman numeral values will be tested for each helper method. 


Modern Roman numerals are written by expressing each digit separately starting with the left most digit and skipping any digit with a value of zero. In Roman numerals 1990 is rendered: 1000=M, 900=CM, 90=XC; resulting in MCMXC. 2008 is written as 2000=MM, 8=VIII; or MMVIII. 1666 uses each Roman symbol in descending order: MDCLXVI.


## Examples
```javascript
RomanNumerals.toRoman(1000); // should return 'M'
RomanNumerals.fromRoman('M'); // should return 1000
```
```coffeescript
RomanNumerals.toRoman(1000) # should return 'M'
RomanNumerals.fromRoman('M') # should return 1000
```
```ruby
RomanNumerals.to_roman(1000) # should return 'M'
RomanNumerals.from_roman('M') # should return 1000
```

```python
RomanNumerals.to_roman(1000) # should return 'M'
RomanNumerals.from_roman('M') # should return 1000
```

```c
to_roman(1000) // should return 'M'
from_roman('M') // should return 1000
```

```c++
RomanNumerals.to_roman(1000) // should return 'M'
RomanNumerals.from_roman('M') // should return 1000
```

```julia
RomanNumerals.toroman(1000) # should return "M"
RomanNumerals.fromroman("M") # should return 1000
```

## Help

| Symbol | Value |
|----------------|
| I	     | 1     |
| V	     | 5     |
| X	     | 10    |
| L	     | 50    |
| C	     | 100   |
| D	     | 500   |
| M	     | 1000  |


## Solutions
#### 🧠 C++
```c++
#include <map>

class
{
    //roman to int
    map<char,int> rtoi =
    {
        {'I',1},
        {'V',5},
        {'X',10},
        {'L',50},
        {'C',100},
        {'D',500},
        {'M',1000},
    };
  
    //int to roman
    map<int,char> itor =
    {
        {1,'I'},
        {5,'V'},
        {10,'X'},
        {50,'L'},
        {100,'C'},
        {500,'D'},
        {1000,'M'},
    };

    //int to roman special cases
    map<int,string> itor_spectial =
    {
        {4,"IV"},
        {9,"IX"},
        {40,"XL"},
        {90,"XC"},
        {400,"CD"},
        {900,"CM"},
    };
  

public:
    int from_roman(string s)
    {
        unsigned res = 0;
        //check char by char and check if it`s double char
        for(size_t i = 0; i < s.size(); ++i)
        {
            //check for double char
            if( i != s.size()-1
                &&
                (
                 (s[i] == 'I' && (s[i+1] == 'V' || s[i+1] == 'X')) ||
                 (s[i] == 'X' && (s[i+1] == 'L' || s[i+1] == 'C')) ||
                 (s[i] == 'C' && (s[i+1] == 'D' || s[i+1] == 'M'))
                )
               )
            {
                    res += rtoi[s[i+1]] - rtoi[s[i]];
                    ++i; //we processed 2 symbols
            }
            //process 1 char
            else
                res+=rtoi[s[i]];

        }
        return res;
    }
  
    string to_roman(int i)
    {
        string result;
        for(auto iter = rbegin(itor); iter != rend(itor); ++iter)
        {
            while(i/iter->first)
            {
                map<int,string>::iterator special_match;
                if( (i < 10   && (special_match = itor_spectial.find(i%10)) != itor_spectial.end()) ||
                    (i < 100  && (special_match = itor_spectial.find(i%100/10*10)) != itor_spectial.end()) ||
                    (i < 1000 && (special_match = itor_spectial.find(i%1000/100*100)) != itor_spectial.end()) )
                {
                  i -= special_match->first;
                  result += special_match->second;
                }
                else
                {
                    i -= iter->first;
                    result.push_back(iter->second);
                }
            }
        }
          
        return result;
    }
} RomanNumerals;
```
