# Number Format

## [Number Format](https://www.codewars.com/kata/565c4e1303a0a006d7000127)

Format any integer provided into a string with "," \(commas\) in the correct places.

**Example:**

```csharp
Kata.NumberFormat(100000); // return "100,000"
Kata.NumberFormat(5678545); // return "5,678,545"
Kata.NumberFormat(-420902); // return "-420,902"
```

```javascript
numberFormat(100000); // return '100,000'
numberFormat(5678545); // return '5,678,545'
numberFormat(-420902); // return '-420,902'
```

```cpp
numberFormat(100000); // return '100,000'
numberFormat(5678545); // return '5,678,545'
numberFormat(-420902); // return '-420,902'
```

```python
number_format(100000); # return '100,000'
number_format(5678545); # return '5,678,545'
number_format(-420902); # return '-420,902'
```

```ruby
number_format(100000); # return '100,000'
number_format(5678545); # return '5,678,545'
number_format(-420902); # return '-420,902'
```

```text
number_format(100000); # return '100,000'
number_format(5678545); # return '5,678,545'
number_format(-420902); # return '-420,902'
```

## Solutions

### 🧠 C++

```cpp
#include<string>
#include <cstdlib>

std::string numberFormat(long long n)
{
  std::string res = n < 0 ? "-" : "",
  input = std::to_string(std::abs(n));

  //first write first 1-3chars
  auto iter = input.begin();
  unsigned shift = input.size()%3 ? input.size()%3 : 3 ;

  res.append(iter,iter+shift);
  iter+=shift;

 //then chunks by 3
  for(;iter< input.end(); iter+=3)
    {
      res.append(",");
      res.append(iter,iter+3);
    }

  return res;

}
```

