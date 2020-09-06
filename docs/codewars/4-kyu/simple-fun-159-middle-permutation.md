# Simple Fun \#159: Middle Permutation

### [Simple Fun \#159: Middle Permutation](https://www.codewars.com/kata/58ad317d1541651a740000c5)

## Task

You are given a string `s`. Every letter in `s` appears once.

Consider all strings formed by rearranging the letters in `s`. After ordering these strings in dictionary order, return the middle term. \(If the sequence has a even length `n`, define its middle term to be the `(n/2)`th term.\)

## Example

For `s = "abc"`, the result should be `"bac"`.

```text
The permutations in order are:
"abc", "acb", "bac", "bca", "cab", "cba"
So, The middle term is "bac".
```

## Input/Output

* `[input]` string `s`

  unique letters \(`2 <= length <= 26`\)

* `[output]` a string

  middle permutation.

### Solutions

#### 🐍 Python

```python
# for 1234567 (odd length)
# it would be 4376521 -- 4(mid) 3(mid-1) 7(from max to min in whats left))6521

# for 1234 (even length)
# it would be 2431 -- 2(mid) 4(from max to min in whats left)31

def middle_permutation(string):
    input_len = len(string)
    string=''.join(sorted(string))
    res = string[(input_len//2)]+string[(input_len//2)-1] if input_len%2 else string[(input_len//2)-1]

    for x in res:
        string = string.replace(x,'')

    res+= ''.join(sorted(string, reverse=True))

    return res
```

