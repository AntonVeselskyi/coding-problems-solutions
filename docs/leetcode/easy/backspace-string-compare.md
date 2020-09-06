# Backspace String Compare

## [Backspace String Compare](https://leetcode.com/problems/backspace-string-compare)

Given two strings `S` and `T`, return if they are equal when both are typed into empty text editors. `#` means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

**Example 1:**

```text

Input: S = "ab#c", T = "ad#c"
Output: true
Explanation: Both S and T become "ac".
```

**Example 2:**

```text

Input: S = "ab##", T = "c#d#"
Output: true
Explanation: Both S and T become "".
```

**Example 3:**

```text

Input: S = "a##c", T = "#a#c"
Output: true
Explanation: Both S and T become "c".
```

**Example 4:**

```text

Input: S = "a#c", T = "b"
Output: false
Explanation: S becomes "c" while T becomes "b".
```

**Note**:

* `1 <= S.length <= 200`
* `1 <= T.length <= 200`
* `S` and `T` only contain lowercase letters and `'#'` characters.

**Follow up:**

* Can you solve it in `O(N)` time and `O(1)` space?

## Solutions

### 🧠 Cpp

```cpp
class Solution
{
public:
    string translate(const string &inputS)
    {
        string S = inputS;
        for(int i = 0; i < S.size(); ++i)
        {
            if(S[i] == '#')
            {
                if(i == 0)
                {
                    S.erase(i,1);
                    i--;
                }
                else
                {
                    S.erase(i-1,2);
                    i-=2;
                }

            }
        }

        return S;
    }
    bool backspaceCompare(string S, string T)
    {
        return translate(S) == translate(T);
    }
};
```

