## [Integers: Recreation One](https://www.codewars.com/kata/55aa075506463dac6600010d)

Divisors of 42 are : 1, 2, 3, 6, 7, 14, 21, 42.
These divisors squared are: 1, 4, 9, 36, 49, 196, 441, 1764.
The sum of the squared divisors is 2500 which is 50 * 50, a square!

Given two integers m, n (1 <= m <= n) we want to find all integers 
between m and n whose sum of squared divisors is itself a square.
42 is such a number.

The result will be an array of arrays or of tuples (in C an array of Pair) or a string, each subarray having two elements,
first the number whose squared divisors is a square and then the sum
of the squared divisors.

#Examples:
```
list_squared(1, 250) --> [[1, 1], [42, 2500], [246, 84100]]
list_squared(42, 250) --> [[42, 2500], [246, 84100]]
```

The form of the examples may change according to the language, see `Example Tests:` for more details.

**Note**

In Fortran - as in any other language - the returned string is not permitted to contain any redundant trailing whitespace: you can use dynamically allocated character strings.



## Solutions
#### 🧠 C++
```c++
#include <vector>
#include <numeric>
#include <sstream>
#include <cmath>
#include <utility>
#include <string>

using ll = long long;

class SumSquaredDivisors
{
public:
    static std::string listSquared(ll m, ll n)
  {
      std::vector<std::pair<ll,ll>> res;
      for(ll i = m; i <=n; i++)
      {
        //find divisors
        std::vector<ll> divisors;
        
        for(ll j = 1; j<=i; ++j)
          if(i%j == 0)
            divisors.push_back(j);
        
        //power all divisors
        std::for_each( divisors.begin(), divisors.end(), [](ll & x){x=std::pow(x,2);});
        
        ll sum_of_elems = std::accumulate(divisors.begin(), divisors.end(), 0);

        double divisors_sqrt = std::sqrt(sum_of_elems);
        if ( divisors_sqrt-(int)divisors_sqrt == 0.0)
          res.push_back({i, sum_of_elems});
      }
      
      //if we found nothing
      if(!res.size())
        return "{}";
      
      //format vector of pairs to string via stringstream
      std::stringstream ss_resstr;
      ss_resstr << "{";
      for (auto k : res)
          ss_resstr<<"{"<<k.first<<", " << k.second << "}, ";
      
      std::string resstr = ss_resstr.str();
      resstr.replace(resstr.end()-2, resstr.end(), "}");
      
      return resstr;
    }
    
};

```
