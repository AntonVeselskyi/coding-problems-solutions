# Delete occurrences of an element if it occurs more than n times

## [Delete occurrences of an element if it occurs more than n times](https://www.codewars.com/kata/554ca54ffa7d91b236000023)

## Enough is enough!

Alice and Bob were on a holiday. Both of them took many pictures of the places they've been, and now they want to show Charlie their entire collection. However, Charlie doesn't like these sessions, since the motive usually repeats. He isn't fond of seeing the Eiffel tower 40 times. He tells them that he will only sit during the session if they show the same motive at most N times. Luckily, Alice and Bob are able to encode the motive as a number. Can you help them to remove numbers such that their list contains each number only up to N times, without changing the order?

## Task

Given a list lst and a number N, create a new list that contains each number of lst at most N times without reordering. For example if N = 2, and the input is \[1,2,3,1,2,1,2,3\], you take \[1,2,3,1,2\], drop the next \[1,2\] since this would lead to 1 and 2 being in the result 3 times, and then take 3, which leads to \[1,2,3,1,2,3\].

```text
## NASM notes

Write the output numbers into the `out` parameter, and return its length.

The input array will contain only integers between 1 and 50 inclusive. Use it to your advantage.
```

```text
For C:
* Assign the return array length to the pointer parameter `*szout`.
* Do not mutate the input array.
```

## Example

```python
  delete_nth ([1,1,1,1],2) # return [1,1]

  delete_nth ([20,37,20,21],1) # return [20,37,21]
```

```ruby
  delete_nth ([1,1,1,1],2) # return [1,1]

  delete_nth ([20,37,20,21],1) # return [20,37,21]
```

```javascript
  deleteNth ([1,1,1,1],2) // return [1,1]

  deleteNth ([20,37,20,21],1) // return [20,37,21]
```

```haskell
deleteNth [20,37,20,21]       1 `shouldBe` [20,37,21]
deleteNth [1,1,3,3,7,2,2,2,2] 3 `shouldBe` [1, 1, 3, 3, 7, 2, 2, 2]
```

```csharp
Kata.DeleteNth (new int[] {20,37,20,21}, 1) // return [20,37,21]
Kata.DeleteNth (new int[] {1,1,3,3,7,2,2,2,2}, 3) // return [1, 1, 3, 3, 7, 2, 2, 2]
```

```fsharp
deleteNth [20;37;20;21] 1 // return [20;37;21]
deleteNth [1;1;3;3;7;2;2;2;2] 3 // return [1;1;3;3;7;2;2;2]
```

```java
EnoughIsEnough.deleteNth(new int[] {20,37,20,21}, 1) // return [20,37,21]
EnoughIsEnough.deleteNth(new int[] {1,1,3,3,7,2,2,2,2}, 3) // return [1, 1, 3, 3, 7, 2, 2, 2]
```

```cpp
deleteNth({20,37,20,21}, 1) // return {20,37,21}
deleteNth({1,1,3,3,7,2,2,2,2}, 3) // return {1, 1, 3, 3, 7, 2, 2, 2}
```

```scala
deleteNth(List(20,37,20,21), 1) // return List(20,37,21)
deleteNth(List(1,1,3,3,7,2,2,2,2), 3) // return List(1, 1, 3, 3, 7, 2, 2, 2)
```

```c
delete_nth(4, {1, 1, 1, 1}, 2, *p)     // returns {1, 1}, 2
delete_nth(4, {20, 37, 20, 21}, 1, *p) // returns {20, 37, 21}, 3
```

## Solutions

### 🧠 C++

```cpp
#include <algorithm>    // std::count
#include <vector>
using std::vector;

vector<int> deleteNth(vector<int> arr, int n)
{
  vector<int> res(arr);
  vector<int> penalty;
  int num, duplicate_num;

  for(int i = 0; i < res.size(); ++i)
  {
    duplicate_num = res[i];
    if( std::count(penalty.begin(), penalty.end(), duplicate_num) )
      continue;
    num = std::count(res.begin(), res.end(), duplicate_num);
    if(num > n)
      {
        penalty.push_back(duplicate_num);
        num = 0;
        for (auto el = res.begin(); el != res.end(); ++el)
        {
                  if (num == n)
                  {
                      res.erase(std::remove(el, res.end(), duplicate_num), res.end());
                      break;
                  }
                  else if (*el == duplicate_num)
                      num++;
        }
      }

  }
  return res;
}
```

