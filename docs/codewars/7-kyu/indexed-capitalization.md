# Indexed capitalization

## [Indexed capitalization](https://www.codewars.com/kata/59cfc09a86a6fdf6df0000f1)

Given a string and an array of integers representing indices, capitalize all letters at the given indices.

For example:

* `capitalize("abcdef",[1,2,5]) = "aBCdeF"`
* `capitalize("abcdef",[1,2,5,100]) = "aBCdeF"`. There is no index 100.

The input will be a lowercase string with no spaces and an array of digits.

Good luck!

Be sure to also try:

[Alternate capitalization](https://www.codewars.com/kata/59cfc000aeb2844d16000075)

[String array revisal](https://www.codewars.com/kata/59f08f89a5e129c543000069)

## Solutions

### 🌔 Lua

```lua
table = require 'table'

myf = function (s,arr) 
  for i=1,#arr do
    j = arr[i]+1 --Lua arr starts from 1
    if j > #s then ::continue:: end
    s = s:sub(1,j-1)..string.upper(s:sub(j,j))..s:sub(j+1,#s);
  end
  return s
end

indexcap = {capitalize = myf}
return indexcap
```

