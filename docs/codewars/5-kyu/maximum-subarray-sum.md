# Maximum subarray sum

## [Maximum subarray sum](https://www.codewars.com/kata/54521e9ec8e60bc4de000d6c)

The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers:

```haskell
maxSequence [-2, 1, -3, 4, -1, 2, 1, -5, 4]
-- should be 6: [4, -1, 2, 1]
```

```javascript
maxSequence([-2, 1, -3, 4, -1, 2, 1, -5, 4])
// should be 6: [4, -1, 2, 1]
```

```python
max_sequence([-2, 1, -3, 4, -1, 2, 1, -5, 4])
# should be 6: [4, -1, 2, 1]
```

```text
(max-sequence [-2, 1, -3, 4, -1, 2, 1, -5, 4])
;; should be 6: [4, -1, 2, 1]
```

```java
Max.sequence(new int[]{-2, 1, -3, 4, -1, 2, 1, -5, 4});
// should be 6: {4, -1, 2, 1}
```

```kotlin
maxSequence(listOf(-2, 1, -3, 4, -1, 2, 1, -5, 4));
// should be 6: listOf(4, -1, 2, 1)
```

```c
maxSequence({-2, 1, -3, 4, -1, 2, 1, -5, 4}, 9)
// should return 6, from sub-array: {4, -1, 2, 1}
```

```cpp
maxSequence({-2, 1, -3, 4, -1, 2, 1, -5, 4});
//should be 6: {4, -1, 2, 1}
```

Easy case is when the list is made up of only positive numbers and the maximum sum is the sum of the whole array. If the list is made up of only negative numbers, return 0 instead.

Empty list is considered to have zero greatest sum. Note that the empty list or array is also a valid sublist/subarray.

## Solutions

### 🐍 Python

```python
def maxSequence(arr):
    if not arr:
      return 0

    #first_positive
    fp, fp_n = -1, 0
    for n, x in enumerate(arr):
        if x <= 0 and fp == -1:
            continue
        elif  fp == -1:
            fp = x
            fp_n = n

    #quality_len
    ql = len(arr[fp_n:])

    #max sum 
    ms = 0


    for n1 in range(ql):
        for n2 in range(1, ql - n1 + 1):

            if sum( arr[fp_n + n1:fp_n + n1 + n2] ) > ms:
                   ms = sum( arr[fp_n + n1:fp_n + n1 +n2] )

    return ms
```

