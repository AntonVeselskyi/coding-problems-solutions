# Sum of the first nth term of Series

## [Sum of the first nth term of Series](https://www.codewars.com/kata/555eded1ad94b00403000071)

## Task:

Your task is to write a function which returns the sum of following series upto nth term\(parameter\).

```text
Series: 1 + 1/4 + 1/7 + 1/10 + 1/13 + 1/16 +...
```

## Rules:

* You need to round the answer to 2 decimal places and return it as String.
* If the given value is 0 then it should return 0.00
* You will only be given Natural Numbers as arguments.

## Examples:

```text
SeriesSum(1) => 1 = "1.00"
SeriesSum(2) => 1 + 1/4 = "1.25"
SeriesSum(5) => 1 + 1/4 + 1/7 + 1/10 + 1/13 = "1.57"
```

**NOTE**: In PHP the function is called `series_sum()`.

## Solutions

### 🧠 C++

```cpp
#include <sstream>
#include <iomanip>  

std::string seriesSum(int n)
{
    if(!n)
      return "0.00";

    float sum = 1;
    for(unsigned i = 0; i+1 != n; i++)
    {
      sum += 1.f/(4+3*i);
    }
    std::stringstream ss;
    ss << std::fixed << std::setprecision(2) << sum;
    return ss.str();
}
```
