## [Backspaces in string](https://www.codewars.com/kata/5727bb0fe81185ae62000ae3)

Assume `"#"` is like a backspace in string. This means that string `"a#bc#d"` actually is `"bd"`

Your task is to process a string with `"#"` symbols.


## Examples

```
"abc#d##c"      ==>  "ac"
"abc##d######"  ==>  ""
"#######"       ==>  ""
""              ==>  ""
```

## Solutions
#### 🧠 C++
```c++
std::string cleanString(const std::string &s)
{
    std::string res = "";
    for(int i = 0; i < s.size(); i++)
    {
      if(s[i] == '#')
        res.pop_back();
      else
        res.push_back(s[i]);
    }
    
    return res;
}
```
