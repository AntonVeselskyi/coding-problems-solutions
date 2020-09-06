# Count vowels

## [Count vowels](https://www.codewars.com/kata/589e281035999ca36a0001ff)

Return the number \(count\) of vowels in the given string.

We will consider a, e, i, o, and u as vowels for this Kata.

## Solutions

### 💲 Shell

```text
echo $(s=${1,,};r=${s//[^aeiou]/};echo ${#r})
```

