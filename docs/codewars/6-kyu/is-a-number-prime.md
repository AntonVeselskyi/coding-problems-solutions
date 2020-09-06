# Is a number prime?

## [Is a number prime?](https://www.codewars.com/kata/5262119038c0985a5b00029f)

Define a function that takes an integer argument and returns logical value `true` or `false` depending on if the integer is a prime.

Per Wikipedia, a prime number \(or a prime\) is a natural number greater than 1 that has no positive divisors other than 1 and itself.

## Requirements

* You can assume you will be given an integer input.
* You can not assume that the integer will be only positive. You may be given negative numbers as well \(or `0`\).
* **NOTE on performance**: There are no fancy optimizations required, but still _the_ most trivial solutions might time out. Numbers go up to 2^31 \(or similar, depends on language version\). Looping all the way up to `n`, or `n/2`, will be too slow.

## Example

```c
is_prime(1)  /* false */
is_prime(2)  /* true  */
is_prime(-1) /* false */
```

```text
mov edi, 1
call is_prime    ; EAX <- 0 (false)

mov edi, 2
call is_prime    ; EAX <- 1 (true)

mov edi, -1
call is_prime    ; EAX <- 0 (false)
```

```cpp
bool isPrime(5) = return true
```

## Solutions

### 🐍 Python

```python
def is_prime(num):
  if num <= 1:
      return False
  for i in range(2,num-1):
      if num%i == 0:
          return False
  return True
```

### 🧠 C++

```cpp
#include <iostream>
#include <math.h>

bool isPrime(int num)
{

  if (num <= 1)
    return false;

  for(int i = 2; i <= sqrt(num); ++i)
    if( num%i == 0 && i != num)
      return false;

  return true;
}
```

